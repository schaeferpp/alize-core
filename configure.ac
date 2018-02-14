AC_INIT([libalize],[3.0],[dev-alize@listes.univ-avignon.fr])
AM_INIT_AUTOMAKE([foreign])

AC_PROG_CXX
AM_PROG_LIBTOOL
AC_PROG_RANLIB
AC_PROG_MAKE_SET
AC_PROG_INSTALL

AC_LIBTOOL_DLOPEN

#CXXFLAGS="-O3 -ffast-math"

AC_ARG_ENABLE(debug, 
		[  --enable-debug	  compile ALIZE with debug information [[default=no]] ], 
		enable_optimize=$enableval, enable_optimize=no)
if test "$enable_optimize" = "yes"; then 
	CXXFLAGS="-g -Wall"
	AC_SUBST(DEBUG,"_debug")
else
	CXXFLAGS="-O3 -ffast-math"
	AC_SUBST(DEBUG,"")
fi

AC_ARG_ENABLE(stacktrace,
              [  --enable-stacktrace enable backward.hpp stacktrace (will probably only work on linux [[default=yes]] ]
              enable_stacktrace=$enableval, enable_stacktrace=yes)
#Enable stacktrace
if test "$enable_stacktrace" = "yes"; then
    AC_MSG_NOTICE("Stacktrace enabled")
    CPPFLAGS="$CPPFLAGS -DBACKWARD_HAS_BFD=1"
    LIBS="$LIBS -lbfd -ldl"
else
    AC_MSG_NOTICE("Stacktrace disabled")
fi


#AC_ARG_ENABLE(lenfence, 
#		[ --enable-debug	compile with debug information [default=no]], 
#		enable_optimize=$enableval, enable_optimize=no)
#if test "$enable_optimize" = "yes"; then 
#	CXXFLAGS="-g -Wall"
#fi

AC_SUBST(OS,`uname -s`)
AC_SUBST(ARCH,`uname -m`)

AC_OUTPUT(Makefile src/Makefile)
