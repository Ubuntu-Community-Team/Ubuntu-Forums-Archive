---
title: "Gettting lightspark working in 10.04 PPC..."
date: 2011-07-17
forum: Apple Hardware Users
---

### Post by Wolfie Lee on 2011-07-17
Well, I am very close, but have hit a brick wall, here. What I would really like is to change the older libxml++-2.6 packages shown as installed in synaptic to the 2.33.1 versions this compile requires...There are other errors, but i think they all stem from having the older package...if not, I'll just take this one step at a time. if the newer packages are out of the question (I am running the 10.04 PPC on an iBook G4, with a freshly updated kernal...just this morning as a matter of fact), I will need to backport those listed commits shown in the lightspark readme file. I have NEVER backported commits, and really have no clue what it even means...lol. A litte help..? I can almost TASTE Youtube working in firefox on this thing...!:)

---

### Post by linuxopjemac on 2011-07-17
This guy just changed the requirements in the source:
[http://www.lduros.net/posts/lightspark-gnulinux-trisquel/](http://www.lduros.net/posts/lightspark-gnulinux-trisquel/)

Apparentely it worked...

You can of course also try to backport libxml++2.6 from Natty into 10.04...
[https://launchpad.net/ubuntu/natty/+source/libxml++2.6/2.33.1-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/libxml++2.6/2.33.1-1ubuntu1)

Let us know how that goes...If you get it working, I could also try it out myself for MintPPC...

---

### Post by Wolfie Lee on 2011-07-20
I'm having a hard time understanding which file in the package needs changed, here, and could not even open some of the files to look at / edit them, if need be. I just have NO experience in backporting, and would need a complete NOOB tutorial on how to do that, so the link to the Natty download really does me no good at all, right now. I apologize for taking so long, I was on my Honeymoon when I posted and the OTHER Hotel we stayed at charged for Internet service, and I was not going to pay for that. I will see about using Ultimate edition to open the other files I could not access in 10.04, and hopefully, that will allow me to find the proper line 156 to change. I am at my sisters computer for today only, using Her Internet, and may not have web access for a while again, after today, but I will keep posting as I can with this one...HOPEFULLY using the Ultimate Edition will get this done TODAY, and I can post a SOLVED!


...More to come...

Thanks for the input!

---

### Post by Wolfie Lee on 2011-07-20
UPDATE:

It's not good... I got the LINE 155 (NOT! line 156, as stated in the lo&#1111;c duros thread that you gave the link for, linuxopjemac) changed in the proper file, which is "CMakeLists.txt". I also made sure to use synaptic to install the other dependencies mentioned there (libboost-dev, and libjpeg-dev)...then i THOUGHT everything was fine, as the build DID finally end with message "Build files have been written to: /home/scott/lightspark-0.5.0~rc1/objs". THEN I tried to do the make and install...no such luck. I have posted the entire output of the attempt to see if ANYONE might be able to help out with this project, but I am losing faith I will ever get flash working on this thing.:(

I was NOT able to find the plugin file mentioned to add the line given (having to do with installing the lighspark plugin system-wide) near the end of the post, and need help, there, as well (MAYBE that is the only thing I need?).

Notice toward the end of the make -install the backends mentioned (the GDK keys q,p,m,and c), as I am thinking maybe just changing the line 155 in the "CMakeLists.txt" file really did not change lighsparks dependency from the v 2.33.1 of libxml to "any version on hand" as I am assuming it was supposed to do...? If not, Can anyone give specific steps to go about implementing those backports, PLEASE?

This is the output:

scott@scott-laptop:~$ cd lightspark-0.5.0~rc1
scott@scott-laptop:~/lightspark-0.5.0~rc1$ cd objs
scott@scott-laptop:~/lightspark-0.5.0~rc1/objs$ cmake -DCMAKE_BUILD_TYPE=Release ..
-- Found gnash path: /usr/bin/gnash
-- Found assembler: /usr/bin/nasm
-- LLVM llvm-config found at: /usr/bin/llvm-config
-- LLVM version: 2.7
-- LLVM CXX flags: -DNDEBUG -D_GNU_SOURCE -D__STDC_LIMIT_MACROS -D__STDC_CONSTANT_MACROS -O2 -fomit-frame-pointer -g -fno-exceptions -fPIC -Woverloaded-virtual
-- LLVM LD flags: -L/usr/lib/llvm/lib  -lpthread -lffi -ldl -lm
-- LLVM core libs: -lLLVMLinker-lLLVMArchive-lLLVMBitWriter-lLLVMBitReader-lLLVMInstrumentation-lLLVMipo-lLLVMTransformUtils-lLLVMipa-lLLVMAnalysis-lLLVMTarget-lLLVMMC-lLLVMCore-lLLVMSupport-lLLVMSystem-L/usr/lib/llvm/lib
-- LLVM JIT libs: -lLLVMPowerPCCodeGen-lLLVMSelectionDAG-lLLVMPowerPCAsmPrinter-lLLVMAsmPrinter-lLLVMPowerPCInfo-lLLVMJIT-lLLVMExecutionEngine-lLLVMCodeGen-lLLVMScalarOpts-lLLVMInstCombine-lLLVMTransformUtils-lLLVMipa-lLLVMAnalysis-lLLVMTarget-lLLVMMC-lLLVMCore-lLLVMSupport-lLLVMSystem-L/usr/lib/llvm/lib
-- LLVM JIT objs: 
-- Found LLVM: /usr/include
-- Configuring done
-- Generating done
-- Build files have been written to: /home/scott/lightspark-0.5.0~rc1/objs
scott@scott-laptop:~/lightspark-0.5.0~rc1/objs$ make
Scanning dependencies of target translations
[  0%] Generating pl.gmo
[  0%] Generating fr.gmo
[  0%] Generating zh_CN.gmo
[  4%] Built target translations
Scanning dependencies of target spark
[  6%] Building CXX object src/CMakeFiles/spark.dir/asobject.cpp.o
/home/scott/lightspark-0.5.0~rc1/src/asobject.cpp: In member function &#8216;void lightspark::variables_map::dumpVariables()&#8217;:
/home/scott/lightspark-0.5.0~rc1/src/asobject.cpp:723: warning: &#8216;kind&#8217; may be used uninitialized in this function
[  7%] Building CXX object src/CMakeFiles/spark.dir/compat.cpp.o
[  9%] Building CXX object src/CMakeFiles/spark.dir/logger.cpp.o
[ 10%] Building CXX object src/CMakeFiles/spark.dir/swf.cpp.o
/home/scott/lightspark-0.5.0~rc1/src/swf.cpp: In member function &#8216;void lightspark::SystemState::createEngines()&#8217;:
/home/scott/lightspark-0.5.0~rc1/src/swf.cpp:621: warning: ignoring return value of &#8216;int pipe(int*)&#8217;, declared with attribute warn_unused_result
[ 12%] Building CXX object src/CMakeFiles/spark.dir/swftypes.cpp.o
[ 13%] Building CXX object src/CMakeFiles/spark.dir/thread_pool.cpp.o
[ 15%] Building CXX object src/CMakeFiles/spark.dir/threading.cpp.o
[ 16%] Building CXX object src/CMakeFiles/spark.dir/timer.cpp.o
[ 18%] Building CXX object src/CMakeFiles/spark.dir/backends/audio.cpp.o
[ 20%] Building CXX object src/CMakeFiles/spark.dir/backends/builtindecoder.cpp.o
[ 21%] Building CXX object src/CMakeFiles/spark.dir/backends/config.cpp.o
[ 23%] Building CXX object src/CMakeFiles/spark.dir/backends/decoder.cpp.o
/home/scott/lightspark-0.5.0~rc1/src/backends/decoder.cpp: In member function &#8216;virtual bool lightspark::FFMpegStreamDecoder::decodeNextFrame()&#8217;:
/home/scott/lightspark-0.5.0~rc1/src/backends/decoder.cpp:697: warning: comparison between signed and unsigned integer expressions
[ 24%] Building CXX object src/CMakeFiles/spark.dir/backends/extscriptobject.cpp.o
[ 26%] Building CXX object src/CMakeFiles/spark.dir/backends/geometry.cpp.o
[ 27%] Building CXX object src/CMakeFiles/spark.dir/backends/glmatrices.cpp.o
[ 29%] Building CXX object src/CMakeFiles/spark.dir/backends/graphics.cpp.o
/home/scott/lightspark-0.5.0~rc1/src/backends/graphics.cpp: In static member function &#8216;static cairo_pattern_t* lightspark::CairoTokenRenderer::FILLSTYLEToCairo(const lightspark::FILLSTYLE&, double)&#8217;:
/home/scott/lightspark-0.5.0~rc1/src/backends/graphics.cpp:507: warning: unused variable &#8216;st&#8217;
[ 30%] Building CXX object src/CMakeFiles/spark.dir/backends/image.cpp.o
[ 32%] Building CXX object src/CMakeFiles/spark.dir/backends/input.cpp.o
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp: In static member function &#8216;static gboolean lightspark::InputThread::worker(GtkWidget*, GdkEvent*, lightspark::InputThread*)&#8217;:
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:75: error: &#8216;GDK_KEY_q&#8217; was not declared in this scope
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:82: error: &#8216;GDK_KEY_p&#8217; was not declared in this scope
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:85: error: &#8216;GDK_KEY_m&#8217; was not declared in this scope
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:94: error: &#8216;GDK_KEY_c&#8217; was not declared in this scope
make[2]: *** [src/CMakeFiles/spark.dir/backends/input.cpp.o] Error 1
make[1]: *** [src/CMakeFiles/spark.dir/all] Error 2
make: *** [all] Error 2
scott@scott-laptop:~/lightspark-0.5.0~rc1/objs$ sudo make install
[sudo] password for scott: 
[  4%] Built target translations
[  6%] Building CXX object src/CMakeFiles/spark.dir/backends/input.cpp.o
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp: In static member function &#8216;static gboolean lightspark::InputThread::worker(GtkWidget*, GdkEvent*, lightspark::InputThread*)&#8217;:
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:75: error: &#8216;GDK_KEY_q&#8217; was not declared in this scope
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:82: error: &#8216;GDK_KEY_p&#8217; was not declared in this scope
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:85: error: &#8216;GDK_KEY_m&#8217; was not declared in this scope
/home/scott/lightspark-0.5.0~rc1/src/backends/input.cpp:94: error: &#8216;GDK_KEY_c&#8217; was not declared in this scope
make[2]: *** [src/CMakeFiles/spark.dir/backends/input.cpp.o] Error 1
make[1]: *** [src/CMakeFiles/spark.dir/all] Error 2
make: *** [all] Error 2
scott@scott-laptop:~/lightspark-0.5.0~rc1/objs$

---

### Post by linuxopjemac on 2011-07-20
I can't really help you as I work with Debian systems, not with Ubuntu.

---

### Post by Wolfie Lee on 2011-07-20
Well, thanks just the same, I got a lot further down the road than I would have on my own...I hope someone else can help out from here, and I just got done downloading the 10.10 PPC ISO and will give that a spin, next, I guess, if I can't get this one playing flash content. I'll give it a few more days in the posts to see if someone can show me where I've gone wrong, and / or let me know how to backport those commits...

---

### Post by linuxopjemac on 2011-07-21
I am very busy lately with my own project, MintPPC. I am working on a completely new version, based on Linux Mint 11 LXDE and Debian Wheezy. This time I try to achieve an iso based installer and a very similar multimedia codec base. At some point I will hit flash and I will also try to port Lightspark into the project. We'll see.

---

### Post by Wolfie Lee on 2011-07-22
Well, I am still hoping someone else can help, here....?

Again, thanks for the info, as it did help a lot compared to what I had done on my own.

---

### Post by linuxopjemac on 2011-07-22
I think you have to backport that libxml++-2.6 package.
Use pbuilder to do that:
[http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html](http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html)

the source is here:
[http://packages.ubuntu.com/source/natty/libxml++2.6](http://packages.ubuntu.com/source/natty/libxml++2.6)

Shouldn't be too difficult...

---

### Post by Wolfie Lee on 2011-07-22
LOL!!!

Not too difficult for YOU, maybe, my friend...but for ME...?It is ALL greek...even what I have read in the documentation ASSUMES, imo, that I can program and have done those sorts of things on a regular basis.

Thanks for trying, but I truly need STEP - BY - STEP instructions in using pbuilder to get the backporting done for me. I am in the dark, here.

---

### Post by linuxopjemac on 2011-07-22
Then ask a for a backport by the Ubuntu team:
[https://launchpad.net/ubuntu/+source/lightspark/+bugs](https://launchpad.net/ubuntu/+source/lightspark/+bugs)

bug should be having a "wishlist" importance.

---

### Post by linuxopjemac on 2011-07-27
any updates ?

---

### Post by Wolfie Lee on 2011-07-31
Thanks, I just don't have the time to get online much anymore...so this will be progressing VERY slowly from now on. I WILL see if the Ubuntu team can't do those backports, or a least compose / or / link me to a good point-by-point tutorial. I am also half tempted to maybe post this problem to the Ultimate Edition forum sites, as well...there may very well be someone there willing and able to help me get this thing on track, even though they don't use any PPC Ubuntu Releases for their OS's, everyone is also as helpful as they can be, when it counts.

So...no real update, and I can't WAIT to get back to having internet service, but times are tough, and me and my new Wife are adjusting as best we can.

I really DO appreciate all you have done, linuxopjemac, so THAX a million for getting me this far.:)

---

### Post by linuxopjemac on 2011-07-31
I tried Lightspark myself, not very promising (see comment)
[http://mac.linux.be/lightspark-050-released](http://mac.linux.be/lightspark-050-released)

---

