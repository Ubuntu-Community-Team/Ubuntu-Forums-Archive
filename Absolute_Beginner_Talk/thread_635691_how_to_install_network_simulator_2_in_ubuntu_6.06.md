---
title: "how to install network simulator 2 in ubuntu 6.06"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by senthil_1234 on 2007-12-09
i m senthil...i m new to linux
lemme mention the site which was used to install ns in ubuntu

[http://www.isi.edu/nsnam/ns/ns-build.html](http://www.isi.edu/nsnam/ns/ns-build.html)

i tried the allinone package
while installing in linux i got the errors displayed below

home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:88: error: for each function it appears in.)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:93: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:109: warning: implicit declaration of function ‘ScreenOfDisplay’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:109: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:109: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:110: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:134: error: ‘firstBorderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:135: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:139: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:139: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:140: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:153: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Get3DBorder’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:193: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:193: error: ‘existingBorderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:193: warning: left-hand operand of comma expression has no effect
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:193: warning: statement with no effect
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:195: error: ‘XGCValues’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:195: error: syntax error before ‘gcValues’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:196: error: ‘XColor’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:197: error: invalid operands to binary *
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:199: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:201: error: request for member ‘borderInit’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:205: error: request for member ‘borderTable’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:205: error: request for member ‘borderTable’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:207: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:210: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:210: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:211: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:233: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:233: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:234: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:235: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:236: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:242: error: ‘None’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:256: error: ‘gcValues’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:257: error: ‘GCForeground’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Draw3DRectangle’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:284: error: syntax error before ‘Drawable’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_NameOf3DBorder’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:331: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:331: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: At top level:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:352: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:354: warning: return type defaults to ‘int’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_3DBorderColor’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:356: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: At top level:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:376: error: syntax error before ‘Tk_3DBorderGC’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:377: warning: return type defaults to ‘int’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_3DBorderGC’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:383: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:383: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:385: error: ‘None’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:402: error: syntax error before ‘None’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Free3DBorder’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:428: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:428: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:429: error: ‘Display’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:429: warning: implicit declaration of function ‘DisplayOfScreen’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:430: error: ‘prevPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:437: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:448: error: ‘None’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘FreeBorderObjProc’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:532: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:532: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘DupBorderObjProc’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:567: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:567: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_SetBackgroundFromBorder’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:599: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:601: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Draw3DPolygon’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:755: error: syntax error before ‘Drawable’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:757: error: syntax error before ‘XPoint’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:769: error: ‘XPoint’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:769: error: syntax error before ‘poly’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:771: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:772: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:772: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:775: error: ‘Display’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:775: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:777: error: ‘None’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:803: error: ‘p1Ptr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:803: error: subscripted value is neither array nor pointer
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:804: error: ‘p2Ptr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:804: error: subscripted value is neither array nor pointer
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:850: error: subscripted value is neither array nor pointer
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:850: warning: value computed is not used
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:850: warning: value computed is not used
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:851: warning: value computed is not used
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:851: warning: value computed is not used
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:862: error: ‘newB1’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:863: error: ‘newB2’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:865: error: ‘poly’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:868: error: ‘b1’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:868: error: ‘b2’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:900: error: ‘perp’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:903: error: ‘c’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:904: error: ‘shift1’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:905: error: ‘shift2’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:919: error: ‘gc’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:923: warning: implicit declaration of function ‘XFillPolygon’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:923: error: ‘Convex’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:924: error: ‘CoordModeOrigin’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Fill3DRectangle’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:963: error: syntax error before ‘Drawable’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:971: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:997: warning: implicit declaration of function ‘XFillRectangle’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:997: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:997: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Fill3DPolygon’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1028: error: syntax error before ‘Drawable’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1030: error: syntax error before ‘XPoint’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1042: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1044: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1044: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1045: error: ‘Complex’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1045: error: ‘CoordModeOrigin’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: At top level:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1070: error: syntax error before ‘TkDisplay’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1070: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1071: error: syntax error before ‘{’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1073: error: syntax error before ‘&’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1073: error: conflicting types for ‘Tcl_InitHashTable’
/home/senthil/ns-allinone-2.31/tcl8.4.14/generic/tclDecls.h:595: error: previous declaration of ‘Tcl_InitHashTable’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1073: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1096: error: syntax error before ‘XPoint’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1096: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1097: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1097: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1102: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1102: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1104: error: syntax error before ‘{’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1127: error: syntax error before ‘if’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1131: error: syntax error before ‘for’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1133: error: conflicting types for ‘cosine’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1129: error: previous declaration of ‘cosine’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1133: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1133: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1134: error: ‘i’ undeclared here (not in a function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1134: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1135: error: syntax error before ‘}’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1138: warning: initialization makes pointer from integer without a cast
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1138: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1138: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1139: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1139: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1139: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1140: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1140: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1140: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1141: error: syntax error before ‘if’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1143: error: redefinition of ‘dy’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1140: error: previous definition of ‘dy’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1143: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1143: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1144: error: syntax error before ‘}’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1149: error: redefinition of ‘dx’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1139: error: previous definition of ‘dx’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1149: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1149: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1150: error: syntax error before ‘}’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1189: error: syntax error before ‘XPoint’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1189: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1190: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1190: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1191: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1191: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1192: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1192: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1193: error: syntax error before ‘*’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1193: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1194: error: syntax error before ‘{’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1203: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1203: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1203: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1203: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1203: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1204: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1204: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1204: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1204: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1204: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1205: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1205: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1205: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1205: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1205: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1206: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1206: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1206: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1206: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1206: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1208: error: syntax error before ‘if’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1211: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1211: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1211: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1211: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1211: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1212: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1212: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1213: error: syntax error before ‘if’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1215: error: redefinition of ‘q’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1212: error: previous definition of ‘q’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1215: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1215: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1216: error: syntax error before ‘}’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1222: error: redefinition of ‘p’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1211: error: previous definition of ‘p’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1222: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1222: error: request for member ‘y’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1222: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1222: error: request for member ‘x’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1222: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1223: error: redefinition of ‘q’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1212: error: previous definition of ‘q’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1223: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1223: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1224: error: syntax error before ‘if’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1226: error: redefinition of ‘q’
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1212: error: previous definition of ‘q’ was here
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1226: error: initializer element is not constant
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1226: warning: data definition has no type or storage class
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1227: error: syntax error before ‘}’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Get3DBorderFromObj’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1262: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1264: error: invalid operands to binary *
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1264: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1277: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1280: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1280: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1281: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1301: error: request for member ‘borderTable’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1301: error: request for member ‘borderTable’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1305: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1307: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1307: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1308: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1388: error: ‘borderPtr’ undeclared (first use in this function)
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1391: error: invalid operands to binary *
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1391: error: syntax error before ‘)’ token
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1394: error: request for member ‘borderTable’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1394: error: request for member ‘borderTable’ in something not a structure or union
/home/senthil/ns-allinone-2.31/tk8.4.14/unix/../generic/tk3d.c:1396: error: syntax error before ‘)’ token
{standard input}: Assembler messages:
{standard input}:13: Error: symbol `q' is already defined
{standard input}:25: Error: symbol `q' is already defined
{standard input}:31: Error: symbol `q' is already defined
{standard input}:37: Error: symbol `p' is already defined
{standard input}:79: Error: symbol `dy' is already defined
{standard input}:85: Error: symbol `dx' is already defined
make: *** [tk3d.o] Error 1
tk8.4.14 make failed! Exiting ...
For problems with Tcl/Tk see [http://www.scriptics.com](http://www.scriptics.com)


wat shld i do to avoid this prob...
since i m new to linux i find installin from pieces is difficult rather than allinone package


tell me a solution to overcome the above problem


help!

---

