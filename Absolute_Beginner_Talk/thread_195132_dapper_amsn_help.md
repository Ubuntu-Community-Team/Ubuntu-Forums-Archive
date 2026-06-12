---
title: "dapper amsn help"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by OrganicPanda on 2006-06-12
hey all, i wouldn't consider myself an absolute begginer but i don't know where else to post... anyway i live life on he bleeding edge and would like to know if anyone can get amsn (with tcl/tk >= 8.5 so fonts look nice) working, i keep getting errors when trying to 'make' tk (i posted before but to no avail) , has anyone got this working yet?

cheers, panda

---

### Post by ????? on 2006-06-12
I installed via Synaptic and it works fine

---

### Post by Kimm on 2006-06-12
?????, The version in Synaptic does not have antialiesed fonts (uses tcl/tk 8.4).

OrganicPanda, if you could tell uss what the errors are, we might be a bit more helpfull :)

---

### Post by OrganicPanda on 2006-06-12
ahh ok sorry i posted the errors in the last thread and it didnt seem to help, but i'll give you a taste (its pretty much all the same as this but Terminal cuts off most of it because its so long )...

```
or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1091: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1091: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1091: warning: data def inition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1092: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1093: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1094: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1095: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1096: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1097: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1098: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1107: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1107: warning: data def inition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1110: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1216: error: syntax err or before ‘GC’
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1217: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1218: error: syntax err or before ‘KeySym’
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1219: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1219: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1219: error: ‘KeySym’ d eclared as function returning a function
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1219: warning: data def inition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1220: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1222: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1222: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1222: warning: data def inition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1224: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1225: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1239: error: syntax err or before ‘XPoint’
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1247: error: syntax err or before ‘}’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1247: warning: data def inition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1252: error: syntax err or before ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkIntDecls.h:1252: warning: data def inition has no type or storage class
In file included from /home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:17,
                 from /home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:16:
/home/panda/Desktop/tk8.5a4/unix/../generic/tkInt.h:1131: error: syntax error be fore ‘XImage’
/home/panda/Desktop/tk8.5a4/unix/../generic/tkInt.h:1151: error: syntax error be fore ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkInt.h:1151: warning: data definiti on has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tkInt.h:1167: error: syntax error be fore ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tkInt.h:1175: error: syntax error be fore ‘*’ token
In file included from /home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:16:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:31: error: syntax error befor e ‘Screen’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:31: warning: no semicolon at end of struct or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:32: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:36: error: syntax error befor e ‘colormap’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:36: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:50: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:50: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:52: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:52: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:55: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:55: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:59: error: syntax error befor e ‘shadow’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:59: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:62: error: syntax error befor e ‘bgGC’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:62: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:64: error: syntax error befor e ‘darkGC’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:64: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:67: error: syntax error befor e ‘lightGC’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:67: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:72: error: conflicting types for ‘nextPtr’
/home/panda/Desktop/tk8.5a4/unix/../generic/tkInt.h:116: error: previous declara tion of ‘nextPtr’ was here
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:77: error: syntax error befor e ‘}’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:77: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:89: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:89: warning: data definition has no type or storage class
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:90: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.h:91: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:31: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:35: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:38: error: syntax error befor e ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Alloc3DBorde rFromObj’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:88: error: ‘borderPtr’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:88: error: (Each undeclared i dentifier is reported only once
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:88: error: for each function it appears in.)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:93: error: syntax error befor e ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:109: warning: implicit declar ation of function ‘ScreenOfDisplay’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:109: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:109: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:110: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:132: error: ‘firstBorderPtr’ undeclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:133: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:137: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:137: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:138: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:151: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Get3DBorder’ :
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:191: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:191: error: ‘existingBorderPt r’ undeclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:191: warning: left-hand opera nd of comma expression has no effect
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:191: warning: statement with no effect
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:193: error: ‘XGCValues’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:193: error: syntax error befo re ‘gcValues’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:194: error: ‘XColor’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:195: error: invalid operands to binary *
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:197: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:199: error: request for membe r ‘borderInit’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:203: error: request for membe r ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:203: error: request for membe r ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:205: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:208: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:208: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:209: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:231: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:231: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:232: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:233: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:234: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:240: error: ‘None’ undeclared  (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:253: error: ‘gcValues’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:254: error: ‘GCForeground’ un declared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:280: error: syntax error befo re ‘Drawable’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Draw3DRectan gle’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:289: error: ‘borderWidth’ und eclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:292: error: ‘height’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:295: error: ‘tkwin’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:295: error: ‘drawable’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:295: error: ‘border’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:296: error: ‘relief’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_NameOf3DBord er’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:326: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:326: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:346: error: syntax error befo re ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:349: warning: return type def aults to ‘int’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_3DBorderColo r’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:350: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:370: error: syntax error befo re ‘Tk_3DBorderGC’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:376: warning: return type def aults to ‘int’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_3DBorderGC’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:377: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:377: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:379: error: ‘None’ undeclared  (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:396: error: syntax error befo re ‘None’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Free3DBorder ’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:421: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:421: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:422: error: ‘Display’ undecla red (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:422: warning: implicit declar ation of function ‘DisplayOfScreen’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:423: error: ‘prevPtr’ undecla red (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:430: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:441: error: ‘None’ undeclared  (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘FreeBorderObjPr oc’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:524: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:524: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘DupBorderObjPro c’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:559: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:559: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_SetBackgroun dFromBorder’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:591: error: syntax error befo re ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:593: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:742: error: syntax error befo re ‘Drawable’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Draw3DPolygo n’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:755: error: ‘XPoint’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:755: error: syntax error befo re ‘poly’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:757: error: syntax error befo re ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:758: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:758: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:761: error: ‘Display’ undecla red (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:761: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:761: error: ‘tkwin’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:763: error: ‘None’ undeclared  (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:771: error: ‘leftRelief’ unde clared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:774: error: ‘borderWidth’ und eclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:775: error: ‘drawable’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:775: error: ‘border’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:775: error: ‘pointPtr’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:775: error: ‘numPoints’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:789: error: ‘p1Ptr’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:790: error: ‘p2Ptr’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:834: warning: value computed is not used
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:834: warning: value computed is not used
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:835: warning: value computed is not used
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:835: warning: value computed is not used
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:847: error: ‘newB1’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:848: error: ‘newB2’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:850: error: ‘poly’ undeclared  (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:853: error: ‘b1’ undeclared ( first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:853: error: ‘b2’ undeclared ( first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:884: error: ‘perp’ undeclared  (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:887: error: ‘c’ undeclared (f irst use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:888: error: ‘shift1’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:889: error: ‘shift2’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:903: error: ‘gc’ undeclared ( first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:907: warning: implicit declar ation of function ‘XFillPolygon’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:907: error: ‘Convex’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:908: error: ‘CoordModeOrigin’  undeclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:946: error: syntax error befo re ‘Drawable’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Fill3DRectan gle’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:955: error: syntax error befo re ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:964: error: ‘relief’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:965: error: ‘borderWidth’ und eclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:975: error: ‘height’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:982: warning: implicit declar ation of function ‘XFillRectangle’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:982: error: syntax error befo re ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:982: error: ‘tkwin’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:982: error: ‘drawable’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:982: error: ‘borderPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:988: error: ‘border’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1012: error: syntax error bef ore ‘Drawable’
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Fill3DPolygo n’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1026: error: syntax error bef ore ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1028: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1028: error: ‘tkwin’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1028: error: ‘drawable’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1028: error: ‘borderPtr’ unde clared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1029: error: ‘pointPtr’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1029: error: ‘numPoints’ unde clared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1029: error: ‘Complex’ undecl ared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1029: error: ‘CoordModeOrigin ’ undeclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1030: error: ‘leftRelief’ und eclared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1031: error: ‘border’ undecla red (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1032: error: ‘borderWidth’ un declared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1054: error: syntax error bef ore ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘BorderInit’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1056: error: request for memb er ‘borderInit’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1057: error: request for memb er ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1079: error: syntax error bef ore ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘ShiftLine’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1116: error: ‘p3Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1116: error: ‘p1Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1117: error: ‘p2Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1132: error: ‘distance’ undec lared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: At top level:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1166: error: syntax error bef ore ‘*’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Intersect’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1180: error: ‘a2Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1180: error: ‘a1Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1180: error: ‘b2Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1180: error: ‘b1Ptr’ undeclar ed (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1195: error: ‘iPtr’ undeclare d (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘Tk_Get3DBorderF romObj’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1239: error: ‘borderPtr’ unde clared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1241: error: invalid operands  to binary *
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1241: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1253: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1256: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1256: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1257: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1277: error: request for memb er ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1277: error: request for memb er ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1281: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1283: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1283: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1284: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1364: error: ‘borderPtr’ unde clared (first use in this function)
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1367: error: invalid operands  to binary *
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1367: error: syntax error bef ore ‘)’ token
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1370: error: request for memb er ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1370: error: request for memb er ‘borderTable’ in something not a structure or union
/home/panda/Desktop/tk8.5a4/unix/../generic/tk3d.c:1372: error: syntax error bef ore ‘)’ token
make: *** [tk3d.o] Error 1

```

i hope it puts a scrollbar there lol

well it looiks asif its just a malformed file but i have no idea how to remedy that

---

### Post by GoBieN on 2006-06-13
same problem for me ! tcl went fine, but tk not

---

### Post by u.b.u.n.t.u on 2006-06-13
[QUOTE=Kimm]?????, The version in Synaptic does not have antialiesed fonts (uses tcl/tk 8.4).

OrganicPanda, if you could tell uss what the errors are, we might be a bit more helpfull :)[/QUOTE]

Do you know how to enable antialiesed fonts? Thanks.

---

### Post by OrganicPanda on 2006-06-13
anti-aliasing of fonts in tcl applications comes with tcl/tk version 8.5 and above so aslong as you have that version then it should be working smooth, the problem is getting it to work in dapper ... well if anyone does get it going then [http://ubuntuforums.org/showthread.php?t=84765]("http://ubuntuforums.org/showthread.php?t=84765")
 walks you through the de-uglify process

---

### Post by u.b.u.n.t.u on 2006-06-13
So there isn't a "download" this and "install" and then you have it? What they describe isn't something someone new to Linux can do. All of that effort just to have anti-aliasing of fonts is a good example of why some people think Linux isn't ready yet.

For me "enough works" so I can get by. A case of the benefits out weighing the disadvantages.

Those instructions assume a lot of prerequisite knowledge.

---

### Post by OrganicPanda on 2006-06-14
well ubuntu natively supports aa fonts but amsn isnt written for linux, it is written for tcl/tk which can be applied to windows/linux/mac etc... , kinda like java so this is an update to get tcl/tk to use aa fonts across all os's that can run tcl/tk applications not a linux specific thing.

anyway back on topic, i am suprised that nobody has this going yet, i thought we had a thriving amsn following here

---

### Post by panurge77 on 2006-06-14
you nedd to do 
```
sudo apt-get build-dep tcl8.4 tk8.4
sudo apt-get install libxft-dev
```
this sould do the trick for compiling tk correctly
you'll also need some other things to run amsn.. so if you never installed it, install the official version just to get all the dependencies

---

### Post by u.b.u.n.t.u on 2006-06-15
Thanks panurge77. Now to wait for a friend to come online to test if it worked.

It looks sharper but that may just be wishful thinking :D

Edit = typos.

---

### Post by u.b.u.n.t.u on 2006-06-15
Correction, the capital W is jagged. So this hasn't worked.

---

### Post by u.b.u.n.t.u on 2006-06-15
Kmess has anti-aliasing by default and the save function of chats is the best I have seen.

Kmess is available via synaptic.

Homepage
[http://kmess.sourceforge.net/](http://kmess.sourceforge.net/)

---

### Post by panurge77 on 2006-06-15
Could you compile tk correctly?
Did you use the --enable-xft on ./configure?
Also... did you compile your amsn? Oficial amsn deb from the repository will use tcl8.4, no mather what... so that does not help you
You need to compile amsn with the proper tcl/tk.

This should do, after you installed the deps:

1- Compiling tcl:
```
./configure --prefix=/usr/local
make
sudo make install
```

2- Compiling tk:
```
./configure --prefix=/usr/local --enable-xft (make sure configure is not telling you it didnt find xft config file. if it tells you so, you're still missing libxft-dev)
make
sudo make install
```

3- compiling amsn (get the svn tarball amsn-dev.tar.gz)
```
./configure --with-tcl=/usr/local/lib --with-tk=/usr/local/lib
make
sudo make install
```

---

### Post by OrganicPanda on 2006-06-16
wow with those instructions i finally managed to get it all installed.... thank you so much panurge77

but now it wont start lol, it looks like its going to but then it just gives up, this is making me quite annoyed lol

when i try running 'amsn' from the terminal it just says 'segmentation fault' and i have no idea what that means

---

### Post by Nikusan on 2006-06-16
You could try just installing the ubuntu package from here: [http://amsn.sourceforge.net/linux-downloads.php](http://amsn.sourceforge.net/linux-downloads.php)

It worked fine for me, good fonts and comes with a theme that is much more at home in ubuntu than the package in the repos.

---

### Post by OrganicPanda on 2006-06-16
the versions availible on the amsn site are seriously old and lacking in features that people want because they are included in the msn windows client, features such as personal messages for example.

damn i wish i knew what a 'Segmentation fault' was and how to fix it

---

### Post by Nikusan on 2006-06-16
aMSN doesn't have personal messages? Then what does it have?

I thought "personal messages" was all msn (and other unofficial msn clients) did?

aMSN in dapper: 0.95-1
package at the homepage: 0.95-3

---

### Post by OrganicPanda on 2006-06-16
no i dont think so, personal messegas are the taglines you can apply to the end of your name (sort of like a secound nick) that appear in the contact list for example my name (with personal messege) could be: 

OrganicPanda - *this is my personal messege*

but during conversation only the first bit shows up like:

OrganicPanda says:
    hello world
My Friend says:
    stop bothering me

etc... etc...

being used to the windows client for so long people will rely on this system

---

### Post by Nikusan on 2006-06-16
Ahh, I misunderstood. Yeah it's a shame it doesn't do that feature, but it's not the end of the world.

---

### Post by panurge77 on 2006-06-16
Make sure you have this installed:
```
sudo apt-get install esound-clients tcltls
```
Then follow this instructions here:
[http://www.ubuntuforums.org/showthread.php?t=26138](http://www.ubuntuforums.org/showthread.php?t=26138)
But use this instead:
```
#!/bin/bash
export LD_ASSUME_KERNEL=2.2.5 && /usr/local/bin/wish8.5 /usr/share/amsn/amsn

```
This should get you into amsn. If you get an error about tls, then:
sudo gedit /usr/lib/tls1.50/pkgIndex.tcl
And change 
[COLOR="Red"]package ifneeded tls 1.5[/COLOR]
To
[COLOR="Red"]package ifneeded tls 1.50
[/COLOR]
Now tell amsn where it is on amsn preferences>advanced> TLS: [COLOR="Red"]/usr/lib[/COLOR]
And make sure you have preferences> others> sound service: [COLOR="Red"]esdplay[/COLOR] $sound
Restart the program and good chatting.

---

### Post by OrganicPanda on 2006-06-18
finally it works, thank god

thank you so much panurge77 for all of your help, now to change the skin and all will be good

---

### Post by panurge77 on 2006-06-19
I've had a hard time too, so I'm glad to help
Clearlooks skin goes well with ubuntu :cool: 
I've found a really cool skin, though

---

### Post by [Nirvana] on 2006-06-19
that didn't work for me, I got an error: 

```
$ sudo apt-get build-dep tcl8.4 tk8.4 Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for tcl8.4
```

---

### Post by panurge77 on 2006-06-20
Maybe you need to enable the extra repos. I dont know because I've alway enabled them. 
sudo gedit /etc/apt/sourcelist
And uncomment all ubuntu.com lines you see there...

---

### Post by Dr.Fix on 2006-06-21
I have aMSN keeping saying my username/password are wrong if I use HTTP method.

Everything works fine using standard authentication... I really need HTTP method, do you know anything about it?

---

### Post by panurge77 on 2006-06-21
On my version (development from two weeks ago) I get a tk error if I try to use http. I don't know if they already corrected it on current version. You can try amsn forum. Someone said gaim beta 2 connects fine with http.

---

### Post by OrganicPanda on 2006-11-23
lol, sorry to reopen such an old thread but I'm now getting the same 'segmentation fault' error on edgy, oh what a kuffufle this linux life is. :p

---

