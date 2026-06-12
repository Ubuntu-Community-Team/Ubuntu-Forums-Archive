---
title: "need help with ARToolKit build"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by caa101 on 2007-03-25
heres the output


```
root@charlie-laptop:/home/charlie/Desktop/ARToolKit# make -k
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/charlie/Desktop/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/charlie/Desktop/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAlloc.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mAlloc.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mFree.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mFree.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocDup.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mAllocDup.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDup.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mDup.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocTrans.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mAllocTrans.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mTrans.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mTrans.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocMul.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mAllocMul.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mMul.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mMul.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocInv.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mAllocInv.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mInv.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mInv.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mSelfInv.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mSelfInv.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mAllocUnit.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mAllocUnit.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mUnit.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mUnit.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDisp.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mDisp.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mDet.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mDet.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include mPCA.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(mPCA.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vAlloc.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(vAlloc.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vDisp.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(vDisp.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vFree.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(vFree.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vHouse.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(vHouse.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vInnerP.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(vInnerP.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include vTridiag.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(vTridiag.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramGet.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(paramGet.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDecomp.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(paramDecomp.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDistortion.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(paramDistortion.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramChangeSize.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(paramChangeSize.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramFile.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(paramFile.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include paramDisp.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(paramDisp.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arDetectMarker.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arGetTransMat.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat2.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arGetTransMat2.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMat3.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arGetTransMat3.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetTransMatCont.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arGetTransMatCont.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arLabeling.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arLabeling.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arDetectMarker2.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arDetectMarker2.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetMarkerInfo.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arGetMarkerInfo.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arGetCode.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arGetCode.o)] Error 127
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -I../../../include arUtil.c
make[2]: cc: Command not found
make[2]: *** [../../libAR.a(arUtil.o)] Error 127
make[2]: Target `all' not remade because of errors.
make[2]: Leaving directory `/home/charlie/Desktop/ARToolKit/lib/SRC/AR'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/charlie/Desktop/ARToolKit/lib/SRC'
make: *** [all] Error 2

```

---

### Post by taurus on 2007-03-25
```
sudo aptitude update
sudo aptitude install build-essential
```
That would give you gcc compiler.

---

### Post by caa101 on 2007-03-25
thanks

---

