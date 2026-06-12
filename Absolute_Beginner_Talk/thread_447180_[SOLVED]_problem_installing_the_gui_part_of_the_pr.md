---
title: "[SOLVED] problem installing the gui part of the program"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by bobbyubun on 2007-05-17
I can not compile the source of the program and i get this Error message when i run make.
I have gl libraries (libGL.so, libGLU.a, libglut.a, etc.) at /usr/lib


/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:537: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:538: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:543: undefined reference to `glPopMatrix'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:547: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:554: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:556: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:558: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:559: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:562: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:564: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:567: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:568: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:571: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:573: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:575: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:576: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:579: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:581: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:583: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:584: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:587: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:591: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:593: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:594: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:597: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:599: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:601: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:602: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:520: undefined reference to `glPopMatrix'
./utils/gui/tracker/libguiutilstracker.a(GUIParameterTracker.o): In function `GUIParameterTracker::GUIParameterTrackerPanel::drawValues()':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:464: undefined reference to `glMatrixMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:465: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:466: undefined reference to `glMatrixMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:467: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:468: undefined reference to `glDisable'
./utils/gui/tracker/libguiutilstracker.a(GUIParameterTracker.o): In function `GUIParameterTracker::GUIParameterTrackerPanel::onPaint(FX::FXObject*, unsigned int, void*)':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:731: undefined reference to `glViewport'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:732: undefined reference to `glClearColor'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:733: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:734: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:735: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:736: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:737: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:738: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:739: undefined reference to `glLineWidth'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:740: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:742: undefined reference to `glClear'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUIParameterTracker.cpp:744: undefined reference to `glFlush'
./utils/gui/tracker/libguiutilstracker.a(GUITLLogicPhasesTrackerWindow.o): In function `GUITLLogicPhasesTrackerWindow::GUITLLogicPhasesTrackerPanel::onConfigure(FX::FXObject*, unsigned int, void*)':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:582: undefined reference to `glViewport'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:583: undefined reference to `glClearColor'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:584: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:585: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:586: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:587: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:588: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:589: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:590: undefined reference to `glLineWidth'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:591: undefined reference to `glPolygonMode'
./utils/gui/tracker/libguiutilstracker.a(GUITLLogicPhasesTrackerWindow.o): In function `GUITLLogicPhasesTrackerWindow::drawValues(GUITLLogicPhasesTrackerWindow::GUITLLogicPhasesTrackerPanel&)':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:291: undefined reference to `glMatrixMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:292: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:293: undefined reference to `glMatrixMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:294: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:295: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:296: undefined reference to `glScaled'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:297: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:299: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:315: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:316: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:317: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:318: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:321: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:323: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:325: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:326: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:331: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:332: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:333: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:334: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:338: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:339: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:340: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:341: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:342: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:399: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:400: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:401: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:395: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:396: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:390: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:391: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:392: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:393: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:394: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:381: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:382: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:383: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:384: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:385: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:422: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:445: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:447: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:449: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:450: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:452: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:453: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:454: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:455: undefined reference to `glEnd'
./utils/gui/tracker/libguiutilstracker.a(GUITLLogicPhasesTrackerWindow.o): In function `GUITLLogicPhasesTrackerWindow::GUITLLogicPhasesTrackerPanel::onPaint(FX::FXObject*, unsigned int, void*)':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:613: undefined reference to `glViewport'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:614: undefined reference to `glClearColor'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:615: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:616: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:617: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:618: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:619: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:620: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:621: undefined reference to `glLineWidth'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:622: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:624: undefined reference to `glClear'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:626: undefined reference to `glFlush'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:149: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:150: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:152: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:153: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:154: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:155: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:156: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:157: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:158: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:159: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:160: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:161: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:162: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:128: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:129: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:130: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:131: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:132: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:133: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:134: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:135: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:136: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:137: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:138: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:139: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:140: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:269: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:270: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:271: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:272: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:273: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:274: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:275: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:254: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:255: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:256: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:257: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:258: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:259: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:260: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawTriangleAtEnd(Line2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:378: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:379: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:380: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:381: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:382: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:383: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:384: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:385: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:386: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledPoly(Position2DVector const&, bool)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:109: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:110: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:114: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:118: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:338: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:344: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:345: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:346: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:347: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:349: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:350: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o):/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:351: more undefined references to `glVertex2d' follow
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:352: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:357: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:358: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:359: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:360: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:362: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:363: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o):/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:364: more undefined references to `glVertex2d' follow
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:365: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledCircle(float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:298: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:304: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:305: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:306: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:307: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:308: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:313: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:314: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:315: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:316: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:317: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:163: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:141: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:276: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:261: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledPoly(Position2DVector const&, bool)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:120: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:120: undefined reference to `glEnd'
./utils/glutils/libglutils.a(polyfonts.o): In function `drawWideChar':
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1004: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1022: undefined reference to `glVertex2f'
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1024: undefined reference to `glEnd'
collect2: ld returned 1 exit status
make[3]: *** [sumo-guisim] Error 1
make[3]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make: *** [all-recursive] Error 1


I would appreciate any help

---

### Post by Hobo Joe on 2007-05-17
Explain more fully what you were doing, and what you typed into the Terminal when this happened.

Also, use code tags.

---

### Post by Delkster on 2007-05-17
Which program are you trying to compile?

Edit: Never mind, it's of course quite evident if I actually read your post. :-)


Anyway, do you have the -dev packages of the OpenGL libraries? You need those for compiling programs that use the OpenGL libraries -- just having the run-time libraries isn't enough. You probably want at least libgl1-mesa-dev and libglu1-mesa-dev.

---

### Post by bobbyubun on 2007-05-17
I am compiling SUMO program([http://sumo.sourceforge.net/index.shtml](http://sumo.sourceforge.net/index.shtml)) that is a traffic simulator. It consist of several programs and a graphic simulator(sumo-guisim).I successfuly run configure but when i run make command (compile) I get the error as follows in the terminal that i run the make:

[I]92: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:293: undefined reference to `glMatrixMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:294: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:295: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:296: undefined reference to `glScaled'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:297: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:299: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:315: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:316: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:317: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:318: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:321: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:323: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:325: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:326: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:331: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:332: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:333: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:334: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:338: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:339: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:340: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:341: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:342: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:399: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:400: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:401: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:395: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:396: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:390: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:391: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:392: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:393: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:394: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:381: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:382: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:383: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:384: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:385: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:422: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:445: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:447: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:449: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:450: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:452: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:453: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:454: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:455: undefined reference to `glEnd'
./utils/gui/tracker/libguiutilstracker.a(GUITLLogicPhasesTrackerWindow.o): In function `GUITLLogicPhasesTrackerWindow::GUITLLogicPhasesTrackerPanel::onPaint(FX::FXObject*, unsigned int, void*)':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:613: undefined reference to `glViewport'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:614: undefined reference to `glClearColor'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:615: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:616: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:617: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:618: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:619: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:620: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:621: undefined reference to `glLineWidth'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:622: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:624: undefined reference to `glClear'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:626: undefined reference to `glFlush'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:149: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:150: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:152: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:153: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:154: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:155: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:156: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:157: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:158: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:159: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:160: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:161: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:162: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:128: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:129: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:130: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:131: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:132: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:133: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:134: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:135: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:136: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:137: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:138: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:139: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:140: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:269: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:270: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:271: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:272: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:273: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:274: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:275: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:254: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:255: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:256: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:257: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:258: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:259: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:260: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawTriangleAtEnd(Line2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:378: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:379: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:380: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:381: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:382: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:383: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:384: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:385: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:386: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledPoly(Position2DVector const&, bool)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:109: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:110: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:114: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:118: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:338: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:344: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:345: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:346: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:347: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:349: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:350: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o):/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:351: more undefined references to `glVertex2d' follow
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:352: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:357: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:358: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:359: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:360: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:362: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:363: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o):/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:364: more undefined references to `glVertex2d' follow
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:365: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledCircle(float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:298: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:304: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:305: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:306: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:307: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:308: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:313: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:314: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:315: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:316: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:317: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:163: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:141: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:276: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:261: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledPoly(Position2DVector const&, bool)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:120: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:120: undefined reference to `glEnd'
./utils/glutils/libglutils.a(polyfonts.o): In function `drawWideChar':
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1004: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1022: undefined reference to `glVertex2f'
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1024: undefined reference to `glEnd'
collect2: ld returned 1 exit status
make[3]: *** [sumo-guisim] Error 1
make[3]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make: *** [all-recursive] Error 1
[/I]

---

### Post by bobbyubun on 2007-05-17
yes I have already run:

sudo apt-get install libgl1-mesa-dev
sudo apt-get install libglu1-mesa-dev
sudo apt-get install mesa-common-dev

and xlibmesa-glu, libx11-dev, libgludev, libsdldev

But I guess i did not install the correct library yet OR i have link problem Or It might be some conflict between X11 and gl

---

### Post by bobbyubun on 2007-05-17
I am still puzzled with these errors since the gl libraries are in /usr/lib

I appreciate help or any hint
thanks-bobby

---

### Post by orb9220 on 2007-05-17
> Note: It seems like some distributions of FOX are built with disabled openGl-support. If you get unresolved references to methods such as "glColor...", "glVertex3f...", etc. during compilation of guisim you have to enable openGL-support before compiling the FOX-library using "./configure --with-opengl=yes --prefix=$HOME && make install"; Still, this is the default normally.

From their page [http://sumo.sourceforge.net/wiki/index.php/LinuxBuild](http://sumo.sourceforge.net/wiki/index.php/LinuxBuild)

---

### Post by bobbyubun on 2007-05-17
I ran the below command and still get the same error:

*./configure --with-xerces-libraries=/usr/local/lib --with-xerces-includes=/usr/local/include/xercesc --with-fox-libraries=/usr/local/lib --with-fox-includes=/usr/local/include/fox-1.4 --with-gdal-libraries=/usr/local/lib --with-gdal-includes=/usr/local/include --with-proj-libraries=/usr/local/lib --with-proj-includes=/usr/local/include/ --with-opengl=yes --prefix=$HOME*&&make

---

### Post by bobbyubun on 2007-05-17
Thanks a lot,

I just understood what you said.i am going to rebuild FOX and re-compile SUMO again

---

### Post by bobbyubun on 2007-05-18
I rebuilt fox with ./configure --with-opengl=yes && make && make install
and then recompiled sumo again and problem is solved,Thanks again,nice job orb

bobby

---

