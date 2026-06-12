---
title: "how to compile TK8.4.2 in Ubuntu 7.10"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by robinwt on 2008-04-14
Hi,guys,
I just installed Tck8.4.2 without problem, however, when it comes to Tk8.4.2
I have seen this error in Ubuntu 7.10:
make
gcc -pipe -rdynamic  tkAppInit.o \
                -L/home/tk8.4.2/unix -ltk8.4 \
                -L/home/tcl8.4.2/unix -ltcl8.4   -ldl -lieee -lm -Wl,-rpath,/usr/local/lib:NONE -o wish
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDrawString'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWindowBorderPixmap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XQueryColors'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XLoadFont'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFree'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XMoveWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeCursor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XStringToKeysym'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateGlyphCursor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XConfigureWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XReconfigureWMWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XAllocClassHint'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XRefreshKeyboardMapping'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGrabServer'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeColormap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XLookupString'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XTextWidth16'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeFont'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateImage'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetClipMask'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `_XInitImageFuncPtrs'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XConvertSelection'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XUngrabPointer'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetWindowProperty'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetFont'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeModifiermap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XEmptyRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XAllocNamedColor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWMNormalHints'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGrabPointer'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGContextFromGC'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetClassHint'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeColors'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSubtractRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XListFonts'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XIconifyWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XTranslateCoordinates'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateColormap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XRootWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XClipBox'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XOpenDisplay'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeFontNames'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetFontProperty'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XListHosts'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCopyArea'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDeleteProperty'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSynchronize'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDrawLine'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWindowBorder'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDestroyWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFillRectangles'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCloseDisplay'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XBell'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFillArc'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetForeground'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFillRectangle'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetGeometry'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XUnmapWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetTransientForHint'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreatePixmapCursor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWMName'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreeGC'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XUngrabServer'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetWMColormapWindows'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XMoveResizeWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDrawLines'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDrawRectangle'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XForceScreenSaver'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XNextEvent'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XRectInRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XKeysymToString'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XResizeWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XMapWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XUngrabKeyboard'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetInputFocus'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateBitmapFromData'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWMColormapWindows'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWindowBackground'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetIconName'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreateGC'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSelectInput'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetInputFocus'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFlush'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetTSOrigin'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XLookupColor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XTextWidth'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSync'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetSelectionOwner'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSendEvent'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XChangeGC'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XWarpPointer'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XWithdrawWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetAtomName'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XPutImage'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFillPolygon'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XLoadQueryFont'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XParseColor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XKeycodeToKeysym'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWMClientMachine'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XIntersectRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWindowBorderWidth'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDefineCursor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetImage'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDestroyRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDrawArc'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWindowBackgroundPixmap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XAllocColor'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCopyPlane'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetModifierMapping'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XInternAtom'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGrabKeyboard'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XQueryPointer'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetVisualInfo'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XVisualIDFromVisual'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XKeysymToKeycode'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetCommand'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XGetWindowAttributes'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XNoOp'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XChangeProperty'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XAllocSizeHints'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetErrorHandler'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XFreePixmap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XDrawString16'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XStringListToTextProperty'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XReparentWindow'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XCreatePixmap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XUnionRectWithRegion'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetClipOrigin'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetDashes'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XQueryTree'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XEventsQueued'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWMHints'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XSetWindowColormap'
/home/tk8.4.2/unix/libtk8.4.so: undefined reference to `XChangeWindowAttributes'
collect2: ld returned 1 exit status
make: *** [wish] Error 1

what I miss out and what I suppose to do next.
Your prompt response is greately appreciated.

Regards/Robin

---

### Post by pedro_orange on 2008-04-14
! Doesn't look pretty.

Have you tried re-extracting the files from the tarball again? Cause it looks like libtk8.4 didn't get extracted properly.

Or, you may have an unmet dependency on Xlib. You could try downloading xlibs-dev and see if that helps.

Good luck

---

