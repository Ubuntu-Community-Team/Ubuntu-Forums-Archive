---
title: "OpenSceneGraph"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-20
Should OpenSceneGraph [http://www.openscenegraph.com/index.php](http://www.openscenegraph.com/index.php) work on 64-bit Feisty 7.04?

It looks like I need it in order to build the Flightgear flightsim from sources.

I can see Flightgear in synaptic, and I've installed it as a downloaded binary package in the past okay. However I'm now trying to build / install it from sources for 2 reasons; firstly to try and get a specific 'plane working, and secondly as a Linux learning experience.

I have successfully checked, and built and installed where neccessary, all of the dependencies for FlightGear compilation except for OSG. 

As a test,
[http://www.opendimension.org/ida/compile.php](http://www.opendimension.org/ida/compile.php)
- won't work for me, errors in make for producer / open threads, no spinning cow :(

I think I've messed it up by previously installing maybe the wrong variants of the OSG components, in maybe the wrong order. I can't seem to get consistently sensible output from make, for any of open producer, osg itself, or open threads.

I did get osg itself (not it's producer or openthreads parts) to look like it had ./configured, ccmake'd and installed at one point

Anyway I'm at the stage where my head is fried with it all, and I'm considering just ditching my current install of Ubuntu, and reloading it from scratch before trying again. Before I do though, is there any simple way to entirely remove all traces of OSG from my system?

I guess what I'm trying to disover is, the Linux equivalent to the old windows gambit of uninstalling a program, then manually searching the older tree for any straggling traces, then running a registry cleaner, then manually hacking through the registry to kill any final references to a prog so that one can truly start again fresh. That's second nature to me in XP but I just am not oriented enough in ubuntu yet to know where to start cleaning up a messed up install. 

I haven't really made a record of exactly what i've done so far in attempting to install OSG, yes, I know that makes a question like this almost impossible to answer but.. well, any infos and suggestions however vague, gladly received!

I have pretty much (attempted to) install all source packages so far, by extracting them from their archives and placing their folders under /home/user/myprogs, then running ./autogen.sh; ./configure; make; make install etc in each package folder's root as appropriate or instructed. OSG itself seemed to want me to use ccmake.

Flightgear itself, ./configures, makes and make installs no problem and spits out a main executable where it's supposed to, on the rare occasions I get the main OSG component (but not OSG's producer or OSG's openthreads) to compile.  Flightgear's executable then refuses to fire up, however.

They've been trying to help me over at the Flightgear forums but it looks like a dead end at the moment. [http://www.flightgear.org/forums/viewtopic.php?p=1279#1279](http://www.flightgear.org/forums/viewtopic.php?p=1279#1279)

Time for a reload of the OS?

---

### Post by SlowButDim on 2007-06-20
> 
As a test,
[http://www.opendimension.org/ida/compile.php](http://www.opendimension.org/ida/compile.php)
- won't work for me, errors in make for producer / open threads, no spinning cow 

This tutorial, that I'm responsible of, is now outdated, sorry about that. I'll fix that soon.

Producer is not used anymore in OSG 2.0.

I *think* that osg should work in 64-bit systems but i'm not sure.

---

### Post by ecs_pf5 on 2007-06-20
Thanks for that info.. well maybe it is outdated but I liked the page anyway :p

So I do not need to worry about trying to install Producer then? That would be one weight off my mind, since it was the one I was finding hardest to get any sense out of.

After trying to install OSG, I get these files in my library areas:

```

link: /usr/local/lib64/libosgViewer.so.11  
target: /usr/local/lib64/libosgViewer.so.2.0.0 
 
link: /home/user/myprogs/OSG/OpenSceneGraph/lib/libosgViewer.so.11 
target: /home/user/myprogs/OSG/OpenSceneGraph/lib/libosgViewer.so.2.0.0 
 
link: /home/user/myprogs/OSG/OpenSceneGraph/src/osgViewer/CMakeFiles/CMakeRelink.dir/libosgViewer.so.11 
target: /home/user/myprogs/OSG/OpenSceneGraph/src/osgViewer/CMakeFiles/CMakeRelink.dir/libosgViewer.so.2.0.0 

```

So it does seem to be trying to do something 64-bittish

But neither the cow nor flightgear seems to want to have any truck with it.

---

### Post by SlowButDim on 2007-06-20
Ok, I updated the tutorial. Hope that works for you. Made in a hurry so may contain errors :p

You may know command ldd which is very handy if there seems to be problem with libraries.
```
ldd /usr/local/bin/osgviewer
```
This should result something like tthis:
```
arihayri@arihayri-desktop:~/programs/build_osg$ ldd /usr/local/bin/osgviewer
        linux-gate.so.1 =>  (0xffffe000)
        libosg.so.11 => /usr/local/lib/libosg.so.11 (0xb7d8f000)
        libosgDB.so.11 => /usr/local/lib/libosgDB.so.11 (0xb7d27000)
        libosgUtil.so.11 => /usr/local/lib/libosgUtil.so.11 (0xb7be0000)
        libosgGA.so.11 => /usr/local/lib/libosgGA.so.11 (0xb7b99000)
        libosgViewer.so.11 => /usr/local/lib/libosgViewer.so.11 (0xb7b24000)
        libosgText.so.11 => /usr/local/lib/libosgText.so.11 (0xb7ae8000)
        libOpenThreads.so.7 => /usr/local/lib/libOpenThreads.so.7 (0xb7ae0000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7abb000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7a3b000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb79af000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb79a6000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb798e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb789c000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb788e000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb77a4000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb777d000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7771000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7630000)
        /lib/ld-linux.so.2 (0xb7f9a000)
        libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb6da9000)
        libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb6da7000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6da3000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb6da0000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6d9a000)
```

---

### Post by SlowButDim on 2007-06-20
DId you find this?
[http://wiki.flightgear.org/flightgear_wiki/index.php?title=OpenSceneGraph](http://wiki.flightgear.org/flightgear_wiki/index.php?title=OpenSceneGraph)

It say that they use SVN-version but I think the stable 2.0 will satisfy also.... but not clear

---

### Post by ecs_pf5 on 2007-06-20
Cheers, I'll take a look at that link now..

Oh dear, that command does not give me good-looking output:

```

user@ubuntu:~$ ldd /usr/local/bin/osgviewer
        libosg.so.11 => not found
        libosgDB.so.11 => not found
        libosgUtil.so.11 => not found
        libosgGA.so.11 => not found
        libosgViewer.so.11 => not found
        libosgText.so.11 => not found
        libOpenThreads.so.7 => not found
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b097146e000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00002b0971689000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0x00002b097190b000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00002b0971acf000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x00002b0971cd9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002b0971ef4000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002b0972202000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b0972413000)
        libm.so.6 => /lib/libm.so.6 (0x00002b0972717000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b097299a000)
        libc.so.6 => /lib/libc.so.6 (0x00002b0972ba8000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b0971251000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b0972ef9000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002b09730fe000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002b0973300000)
user@ubuntu:~$ 


```Yet I can find libosgViewer.so.11 as a link to libosgViewer.so.2.0.0 in my /lib64/

not in /lib/ though..


[edit]

yes.. the link you posted up there ^, that's the one I was following. I used the top set of instructions:

```
mkdir build.osg
cd build.osg
ccmake ../path/to/osg/source
make
make install

```but because fg executable still complained it couldn't find the viewer library, that's when I started trying to install Producer and OpenThreads after-the-event.

(they say the order is important so I figure that is where I have broken it)

I'll go back & take another look at your tutorial.. if still no joy, I'll try a reload of Ubuntu. 

I'm all backed up anyway so it causes no probs to do so.

[edit]

ok using your page, so far so good

```

cmake ../OpenSceneGraph  -DCMAKE_BUILD_TYPE=Release
 make

```6%..7%..8%.. seems to be going through make okay so far..
...20%... I'll go have a cup of tea and a biscuit, back soon....

---

### Post by SlowButDim on 2007-06-20
> Oh dear, that command does not give me good-looking output:

```

user@ubuntu:~$ ldd /usr/local/bin/osgviewer
        libosg.so.11 => not found
        libosgDB.so.11 => not found
        libosgUtil.so.11 => not found
        libosgGA.so.11 => not found
        libosgViewer.so.11 => not found
        libosgText.so.11 => not found
        libOpenThreads.so.7 => not found
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b097146e000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00002b0971689000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0x00002b097190b000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00002b0971acf000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x00002b0971cd9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002b0971ef4000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002b0972202000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b0972413000)
        libm.so.6 => /lib/libm.so.6 (0x00002b0972717000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b097299a000)
        libc.so.6 => /lib/libc.so.6 (0x00002b0972ba8000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b0971251000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b0972ef9000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002b09730fe000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002b0973300000)
user@ubuntu:~$ 


```Yet I can find libosgViewer.so.11 as a link to libosgViewer.so.2.0.0 in my /lib64/

not in /lib/ though..

Just a guess:
```
export LD_LIBRARY_PATH=/usr/local/lib64
```

> 

[edit]

yes.. the link you posted up there ^, that's the one I was following. I used the top set of instructions:

```
mkdir build.osg
cd build.osg
ccmake ../path/to/osg/source
make
make install

```but because fg executable still complained it couldn't find the viewer library, that's when I started trying to install Producer and OpenThreads after-the-event.

(they say the order is important so I figure that is where I have broken it)

if your compilation went through nicely then I think you had OSG right. Maybe the problem was that FlightGear just did not know where to look OSG? Any errors thrown out?
> 

I'll go back & take another look at your tutorial.. if still no joy, I'll try a reload of Ubuntu. 

I'm all backed up anyway so it causes no probs to do so.

If you succeed, then please share your knowledge! I'm also interested of FlighGear. It is just now I don't have time to dive in :)

---

### Post by ecs_pf5 on 2007-06-20
The error given by fgfs when failing to start is just:

```

error while loading shared libraries: libosgViewer.so.11: cannot open shared object file: No such file or directory 

```doing the sudo make install now at your page, still seems to be all going well..

[edit]

ok every instruction at your page worked perfectly. When I tried to spin the cow though....
```

user@ubuntu:~/Desktop/OSG/build$ export PATH=${PATH}:/usr/local/share/OpenSceneGraph/bin
user@ubuntu:~/Desktop/OSG/build$ export OSG_FILE_PATH=/home/user/Desktop/OSG/OpenSceneGraph-Data
user@ubuntu:~/Desktop/OSG/build$ export LD_LIBRARY_PATH=/usr/local/lib
user@ubuntu:~/Desktop/OSG/build$ osgviewer cow.osg
osgviewer: error while loading shared libraries: 
libosg.so.11: cannot open shared object file: No such file or directory

```but then I did

```

user@ubuntu:~$ export LD_LIBRARY_PATH=/usr/local/lib64
user@ubuntu:~$ osgviewer cow.osg
Warning: could not find file "cow.osg"
osgviewer: No data loaded
user@ubuntu:~$ 

```so I must have a path wrong or something but it looks good


[edit]

then..

```

user@ubuntu:~$ export LD_LIBRARY_PATH=/usr/local/lib64
user@ubuntu:~$ osgviewer cow.osg
Warning: could not find file "cow.osg"
osgviewer: No data loaded
user@ubuntu:~$ cd /home/user/Desktop/OSG/OpenSceneGraph-Data
user@ubuntu:~/Desktop/OSG/OpenSceneGraph-Data$ osgviewer cow.osg
user@ubuntu:~/Desktop/OSG/OpenSceneGraph-Data$ 

```[B]






THE COW SPINS NOW hahahaha [/B]:lol:[B] - excellent - really, thanks for all your help.






[/B]
Flightgear still can't seem to find it though:

```

user@ubuntu:~$ cd /home/user/myprogs/FlightGear-0.9/source/src/Main
user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$ fgfs
fgfs: error while loading shared libraries: libosgViewer.so.11: cannot open shared object file: No such file or directory
user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$ fgfs --fg-root=/home/user/myprogs/FlightGear-0.9
fgfs: error while loading shared libraries: libosgViewer.so.11: cannot open shared object file: No such file or directory
user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$

```maybe I should recompile it again.

weird though, still getting

```

user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$ ldd /usr/local/bin/osgviewer
        libosg.so.11 => not found
        libosgDB.so.11 => not found
        libosgUtil.so.11 => not found
        libosgGA.so.11 => not found
        libosgViewer.so.11 => not found
        libosgText.so.11 => not found
        libOpenThreads.so.7 => not found

```ahh..

```

user@ubuntu:~$ export LD_LIBRARY_PATH=/usr/local/lib64
user@ubuntu:~$ cd /home/user/myprogs/FlightGear-0.9/source/src/Main
user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$ fgfs


Base package check failed ... Found version [none] at: /usr/local/share/FlightGear
Please upgrade to version: 0.9.11
user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$ 

```I bet the cow doesn't spin anymore now lol

yeah, I lost the cow.

```

user@ubuntu:~$ cd /home/user/Desktop/OSG/OpenSceneGraph-Data
user@ubuntu:~/Desktop/OSG/OpenSceneGraph-Data$ osgviewer cow.osg
osgviewer: error while loading shared libraries: libosg.so.11: cannot open shared object file: No such file or directory
user@ubuntu:~/Desktop/OSG/OpenSceneGraph-Data$ 

```

---

### Post by SlowButDim on 2007-06-20
> THE COW SPINS NOW hahahaha  - excellent - really, thanks for all your help.

Great!

> yeah, I lost the cow.

Ok, when you export environment variable, it stays there only as long your terminal session is on. So you need to make it permanent.

Find a file called .bashrc and add those exports at the end of that file. .bashrc is executed avery time you open terminal and your environment variables are then set.

Almost there. Try to run fgfs again when your environment variables are set. If that doesn't work, then there must be away to tell it where to look. 

I'll have a look tomorrow, if there is no luck.

---

### Post by ecs_pf5 on 2007-06-20
Sorry, for some reason I thought I was having to put different environment strings in for cow and fg.

No they both work just fine off LD_LIBRARY_PATH=/usr/local/lib64

Setting them permanently in the manner you describe sounds good though, just the same.

The FG message

```

Base package check failed ... Found version [none] at: /usr/local/share/FlightGear
Please upgrade to version: 0.9.11

```is persistent though. I'll try a recompile.

[edit]

found .bashrc, added the 3 paths from your page, all works fine except that weird FG error - hopefully fixable with forthcoming recompile. cross fingers & hope.

```

user@ubuntu:~$ osgviewer cow.osg (<----- yep, got the cow)
user@ubuntu:~$ fgfs


Base package check failed ... Found version [none] at: /usr/local/share/FlightGear
Please upgrade to version: 0.9.11
user@ubuntu:~$ 

```ok reran ./autogen.sh;./configure;make;make install to rebuild & reinstall FG.

used a slightly different syntax for the -fg-root= option, and it ran :lol: hurrah

then it core dumped :( boo


step forward though


```

user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$  fgfs --fg-root=/home/user/myprogs/FlightGear-0.9
*** glibc detected *** fgfs: free(): invalid pointer: 0x000000000107c830 ***
======= Backtrace: =========
/lib/libc.so.6[0x2aeaa4511b23]
/lib/libc.so.6(cfree+0x8c)[0x2aeaa451526c]
/usr/local/lib64/libosg.so.11(_ZN3osg16DrawArrayLengthsD0Ev+0x3c)[0x2aeaa195d80c]
/usr/local/lib64/libosgUtil.so.11(_ZN7osgUtil11TessellatorD1Ev+0x1d2)[0x2aeaa109ade2]
/usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so(_ZN4ac3d10SurfaceBin8finalizeERKNS_12MaterialDataERKNS_11TextureDataE+0x9a9)[0x2aaaaaac9359]
/usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so(_ZN4ac3d10readObjectERSiRNS_8FileDataERKN3osg7MatrixdENS_11TextureDataE+0x18e0)[0x2aaaaaabffd0]
/usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so(_ZN4ac3d10readObjectERSiRNS_8FileDataERKN3osg7MatrixdENS_11TextureDataE+0x27d3)[0x2aaaaaac0ec3]
/usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so(_ZN4ac3d8readFileERSiPKN5osgDB12ReaderWriter7OptionsE+0xf5)[0x2aaaaaac1355]
/usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so(_ZNK14ReaderWriterAC8readNodeERSiPKN5osgDB12ReaderWriter7OptionsE+0xed)[0x2aaaaaad039d]
/usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so(_ZNK14ReaderWriterAC8readNodeERKSsPKN5osgDB12ReaderWriter7OptionsE+0x398)[0x2aaaaaacd2d8]
/usr/local/lib64/libosgDB.so.11(_ZNK5osgDB8Registry15ReadNodeFunctor6doReadERNS_12ReaderWriterE+0x1c)[0x2aeaa132b10c]
/usr/local/lib64/libosgDB.so.11(_ZN5osgDB8Registry4readERKNS0_11ReadFunctorE+0xd7c)[0x2aeaa1328c2c]
/usr/local/lib64/libosgDB.so.11(_ZN5osgDB8Registry18readImplementationERKNS0_11ReadFunctorEb+0x4cd)[0x2aeaa132a40d]
/usr/local/lib64/libosgDB.so.11(_ZN5osgDB8Registry22readNodeImplementationERKSsPKNS_12ReaderWriter7OptionsE+0x85)[0x2aeaa132aa45]
fgfs[0x8ea466]
/usr/local/lib64/libosgDB.so.11(_ZN5osgDB12readNodeFileERKSsPKNS_12ReaderWriter7OptionsE+0x44)[0x2aeaa1314b24]
fgfs[0x8e27a9]
fgfs[0x7a9104]
fgfs[0x7a8a50]
fgfs[0x41fab5]
fgfs[0x464042]
/usr/lib/libglut.so.3(glutMainLoop+0x87)[0x2aeaa228dbf7]
fgfs[0x41f20a]
fgfs[0x41e39d]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2aeaa44bf8e4]
fgfs(_ZN7puGroup4drawEii+0xe9)[0x41e1b9]
======= Memory map: ========
00400000-00aaa000 r-xp 00000000 08:05 2031619                            /usr/local/bin/fgfs
00caa000-00cb8000 rw-p 006aa000 08:05 2031619                            /usr/local/bin/fgfs
00cb8000-0507b000 rw-p 00cb8000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rwxp 40001000 00:00 0 
2aaaaaaab000-2aaaaaad6000 r-xp 00000000 08:05 688276                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so
2aaaaaad6000-2aaaaacd5000 ---p 0002b000 08:05 688276                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so
2aaaaacd5000-2aaaaacd7000 rw-p 0002a000 08:05 688276                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_ac.so
2aaaac000000-2aaaac021000 rw-p 2aaaac000000 00:00 0 
2aaaac021000-2aaab0000000 ---p 2aaaac021000 00:00 0 
2aea9fc12000-2aea9fc2e000 r-xp 00000000 08:05 98319                      /lib/ld-2.5.so
2aea9fc2e000-2aea9fc31000 rw-p 2aea9fc2e000 00:00 0 
2aea9fe2d000-2aea9fe2f000 rw-p 0001b000 08:05 98319                      /lib/ld-2.5.so
2aea9fe2f000-2aea9fe4d000 r-xp 00000000 08:05 41080                      /usr/lib/libplibpuaux.so.1.8.4
2aea9fe4d000-2aeaa004d000 ---p 0001e000 08:05 41080                      /usr/lib/libplibpuaux.so.1.8.4
2aeaa004d000-2aeaa004f000 rw-p 0001e000 08:05 41080                      /usr/lib/libplibpuaux.so.1.8.4
2aeaa004f000-2aeaa007d000 r-xp 00000000 08:05 41077                      /usr/lib/libplibpu.so.1.8.4
2aeaa007d000-2aeaa027d000 ---p 0002e000 08:05 41077                      /usr/lib/libplibpu.so.1.8.4
2aeaa027d000-2aeaa0280000 rw-p 0002e000 08:05 41077                      /usr/lib/libplibpu.so.1.8.4
2aeaa0280000-2aeaa0281000 rw-p 2aeaa0280000 00:00 0 
2aeaa0281000-2aeaa0296000 r-xp 00000000 08:05 41074                      /usr/lib/libplibfnt.so.1.8.4
2aeaa0296000-2aeaa0495000 ---p 00015000 08:05 41074                      /usr/lib/libplibfnt.so.1.8.4
2aeaa0495000-2aeaa049a000 rw-p 00014000 08:05 41074                      /usr/lib/libplibfnt.so.1.8.4
2aeaa049a000-2aeaa04a2000 r-xp 00000000 08:05 41075                      /usr/lib/libplibnet.so.1.8.4
2aeaa04a2000-2aeaa06a1000 ---p 00008000 08:05 41075                      /usr/lib/libplibnet.so.1.8.4
2aeaa06a1000-2aeaa06a2000 rw-p 00007000 08:05 41075                      /usr/lib/libplibnet.so.1.8.4
2aeaa06a2000-2aeaa06a3000 rw-p 2aeaa06a2000 00:00 0 
2aeaa06a3000-2aeaa06b6000 r-xp 00000000 08:05 41071                      /usr/lib/libplibsg.so.1.8.4
2aeaa06b6000-2aeaa08b5000 ---p 00013000 08:05 41071                      /usr/lib/libplibsg.so.1.8.4
2aeaa08b5000-2aeaa08b6000 rw-p 00012000 08:05 41071                      /usr/lib/libplibsg.so.1.8.4
2aeaa08b6000-2aeaa08ba000 r-xp 00000000 08:05 41079                      /usr/lib/libplibul.so.1.8.4
2aeaa08ba000-2aeaa0aba000 ---p 00004000 08:05 41079                      /usr/lib/libplibul.so.1.8.4
2aeaa0aba000-2aeaa0abb000 rw-p 00004000 08:05 41079                      /usr/lib/libplibul.so.1.8.4
2aeaa0abb000-2aeaa0b36000 r-xp 00000000 08:05 202043                     /usr/local/lib64/libosgViewer.so.2.0.0
2aeaa0b36000-2aeaa0d35000 ---p 0007b000 08:05 202043                     /usr/local/lib64/libosgViewer.so.2.0.0
2aeaa0d35000-2aeaa0d3c000 rw-p 0007a000 08:05 202043                     /usr/local/lib64/libosgViewer.so.2.0.0
2aeaa0d3c000-2aeaa0d3d000 rw-p 2aeaa0d3c000 00:00 0 
2aeaa0d3d000-2aeaa0d76000 r-xp 00000000 08:05 202031                     /usr/local/lib64/libosgFX.so.2.0.0
2aeaa0d76000-2aeaa0f75000 ---p 00039000 08:05 202031                     /usr/local/lib64/libosgFX.so.2.0.0
2aeaa0f75000-2aeaa0f78000 rw-p 00038000 08:05 202031                     /usr/local/lib64/libosgFX.so.2.0.0
2aeaa0f78000-2aeaa10d0000 r-xp 00000000 08:05 202016                     /usr/local/lib64/libosgUtil.so.2.0.0
2aeaa10d0000-2aeaa12cf000 ---p 00158000 08:05 202016                     /usr/local/lib64/libosgUtil.so.2.0.0
2aeaa12cf000-2aeaa12dd000 rw-p 00157000 08:05 202016                     /usr/local/lib64/libosgUtil.so.2.0.0
2aeaa12dd000-2aeaa1345000 r-xp 00000000 08:05 202013                     /usr/local/lib64/libosgDB.so.2.0.0
2aeaa1345000-2aeaa1545000 ---p 00068000 08:05 202013                     /usr/local/lib64/libosgDB.so.2.0.0
2aeaa1545000-2aeaa1548000 rw-p 00068000 08:05 202013                     /usr/local/lib64/libosgDB.so.2.0.0
2aeaa1548000-2aeaa1549000 rw-p 2aeaa1548000 00:00 0 
2aeaa1549000-2aeaa15fa000 r-xp 00000000 08:05 202028                     /usr/local/lib64/libosgSim.so.2.0.0
2aeaa15fa000-2aeaa17fa000 ---p 000b1000 08:05 202028                     /usr/local/lib64/libosgSim.so.2.0.0
2aeaa17fa000-2aeaa1800000 rw-p 000b1000 08:05 202028                     /usr/local/lib64/libosgSim.so.2.0.0
2aeaa1800000-2aeaa1a24000 r-xp 00000000 08:05 202010                     /usr/local/lib64/libosg.so.2.0.0
2aeaa1a24000-2aeaa1c24000 ---p 00224000 08:05 202010                     /usr/local/lib64/libosg.so.2.0.0
2aeaa1c24000-2aeaa1c34000 rw-p 00224000 08:05 202010                     /usr/local/lib64/libosg.so.2.0.0
2aeaa1c34000-2aeaa1c35000 rw-p 2aeaa1c34000 00:00 0 
2aeaa1c35000-2aeaa1c3b000 r-xp 00000000 08:05 202007                     /usr/local/lib64/libOpenThreads.so.1.9.5
2aeaa1c3b000-2aeaa1e3b000 ---p 00006000 08:05 202007                     /usr/local/lib64/libOpenThreads.so.1.9.5
2aeaa1e3b000-2aeaa1e3c000 rw-p 00006000 08:05 202007                     /usr/local/lib64/libOpenThreads.so.1.9.5
2aeaa1e3c000-2aeaa1e3d000 rw-p 2aeaa1e3c000 00:00 0 
2aeaa1e3d000-2aeaa1e52000 r-xp 00000000 08:05 98339                      /lib/libpthread-2.5.so
2aeaa1e52000-2aeaa2052000 ---p 00015000 08:05 98339                      /lib/libpthread-2.5.so
2aeaa2052000-2aeaa2054000 rw-p 00015000 08:05 98339                      /lib/libpthread-2.5.so
2aeaa2054000-2aeaa2058000 rw-p 2aeaa2054000 00:00 0 
2aeaa2058000-2aeaa206e000 r-xp 00000000 08:05 34825                      /usr/lib/libz.so.1.2.3
2aeaa206e000-2aeaa226d000 ---p 00016000 08:05 34825                      /usr/lib/libz.so.1.2.3
2aeaa226d000-2aeaa226e000 rw-p 00015000 08:05 34825                      /usr/lib/libz.so.1.2.3
2aeaa226e000-2aeaa22a9000 r-xp 00000000 08:05 39334                      /usr/lib/libglut.so.3.8.0
2aeaa22a9000-2aeaa23a8000 ---p 0003b000 08:05 39334                      /usr/lib/libglut.so.3.8.0
2aeaa23a8000-2aeaa23b1000 rw-p 0003a000 08:05 39334                      /usr/lib/libglut.so.3.8.0
2aeaa23b1000-2aeaa23b2000 rw-p 2aeaa23b1000 00:00 0 
2aeaa23b2000-2aeaa2432000 r-xp 00000000 08:05 39332                      /usr/lib/libGLU.so.1.3.060502
2aeaa2432000-2aeaa2632000 ---p 00080000 08:05 39332                      /usr/lib/libGLU.so.1.3.060502
2aeaa2632000-2aeaa2634000 rw-p 00080000 08:05 39332                      /usr/lib/libGLU.so.1.3.060502
2aeaa2634000-2aeaa26d2000 r-xp 00000000 08:05 2343338                    /usr/lib/libGL.so.1.2
2aeaa26d2000-2aeaa27d1000 ---p 0009e000 08:05 2343338                    /usr/lib/libGL.so.1.2
2aeaa27d1000-2aeaa27f1000 rw-p 0009d000 08:05 2343338                    /usr/lib/libGL.so.1.2
2aeaa27f1000-2aeaa27f7000 rw-p 2aeaa27f1000 00:00 0 
2aeaa27f7000-2aeaa280e000 r-xp 00000000 08:05 36994                      /usr/lib/libXmu.so.6.2.0
2aeaa280e000-2aeaa2a0e000 ---p 00017000 08:05 36994                      /usr/lib/libXmu.so.6.2.0
2aeaa2a0e000-2aeaa2a10000 rw-p 00017000 08:05 36994                      /usr/lib/libXmu.so.6.2.0
2aeaa2a10000-2aeaa2a11000 rw-p 2aeaa2a10000 00:00 0 
2aeaa2a11000-2aeaa2a6d000 r-xp 00000000 08:05 36931                      /usr/lib/libXt.so.6.0.0
2aeaa2a6d000-2aeaa2c6c000 ---p 0005c000 08:05 36931                      /usr/lib/libXt.so.6.0.0
2aeaa2c6c000-2aeaa2c72000 rw-p 0005b000 08:05 36931                      /usr/lib/libXt.so.6.0.0
2aeaa2c72000-2aeaa2c73000 rw-p 2aeaa2c72000 00:00 0 
2aeaa2c73000-2aeaa2c7c000 r-xp 00000000 08:05 36929                      /usr/lib/libSM.so.6.0.0
2aeaa2c7c000-2aeaa2e7c000 ---p 00009000 08:05 36929                      /usr/lib/libSM.so.6.0.0
2aeaa2e7c000-2aeaa2e7d000 rw-p 00009000 08:05 36929                      /usr/lib/libSM.so.6.0.0
2aeaa2e7d000-2aeaa2e94000 r-xp 00000000 08:05 36927                      /usr/lib/libICE.so.6.3.0
2aeaa2e94000-2aeaa3093000 ---p 00017000 08:05 36927                      /usr/lib/libICE.so.6.3.0
2aeaa3093000-2aeaa3095000 rw-p 00016000 08:05 36927                      /usr/lib/libICE.so.6.3.0
2aeaa3095000-2aeaa3099000 rw-p 2aeaa3095000 00:00 0 
2aeaa3099000-2aeaa30a1000 r-xp 00000000 08:05 36959                      /usr/lib/libXi.so.6.0.0
2aeaa30a1000-2aeaa32a1000 ---p 00008000 08:05 36959                      /usr/lib/libXi.so.6.0.0
2aeaa32a1000-2aeaa32a2000 rw-p 00008000 08:05 36959                      /usr/lib/libXi.so.6.0.0
2aeaa32a2000-2aeaa32b2000 r-xp 00000000 08:05 36867                      /usr/lib/libXext.so.6.4.0
2aeaa32b2000-2aeaa34b2000 ---p 00010000 08:05 36867                      /usr/lib/libXext.so.6.4.0
2aeaa34b2000-2aeaa34b3000 rw-p 00010000 08:05 36867                      /usr/lib/libXext.so.6.4.0
2aeaa34b3000-2aeaa35b9000 r-xp 00000000 08:05 36865                      /usr/lib/libX11.so.6.2.0
2aeaa35b9000-2aeaa37b9000 ---p 00106000 08:05 36865                      /usr/lib/libX11.so.6.2.0
2aeaa37b9000-2aeaa37c0000 rw-p 00106000 08:05 36865                      /usr/lib/libX11.so.6.2.0
2aeaa37c0000-2aeaa37c1000 rw-p 2aeaa37c0000 00:00 0 
2aeaa37c1000-2aeaa37c3000 r-xp 00000000 08:05 98328                      /lib/libdl-2.5.so
2aeaa37c3000-2aeaa39c3000 ---p 00002000 08:05 98328                      /lib/libdl-2.5.so
2aeaa39c3000-2aeaa39c5000 rw-p 00002000 08:05 98328                      /lib/libdl-2.5.so
2aeaa39c5000-2aeaa39ca000 r-xp 00000000 08:05 41068                      /usr/lib/libalut.so.0.0.0
2aeaa39ca000-2aeaa3ac9000 ---p 00005000 08:05 41068                      /usr/lib/libalut.so.0.0.0
2aeaa3ac9000-2aeaa3acc000 rw-p 00004000 08:05 41068                      /usr/lib/libalut.so.0.0.0
2aeaa3acc000-2aeaa3b05000 r-xp 00000000 08:05 41066                      /usr/lib/libopenal.so.0.0.0
2aeaa3b05000-2aeaa3d05000 ---p 00039000 08:05 41066                      /usr/lib/libopenal.so.0.0.0
2aeaa3d05000-2aeaa3d07000 rw-p 00039000 08:05 41066                      /usr/lib/libopenal.so.0.0.0
2aeaa3d07000-2aeaa3d0d000 rw-p 2aeaa3d07000 00:00 0 
2aeaa3d0d000-2aeaa3d8e000 r-xp 00000000 08:05 98329                      /lib/libm-2.5.so
2aeaa3d8e000-2aeaa3f8d000 ---p 00081000 08:05 98329                      /lib/libm-2.5.so
2aeaa3f8d000-2aeaa3f8f000 rw-p 00080000 08:05 98329                      /lib/libm-2.5.so
2aeaa3f8f000-2aeaa4078000 r-xp 00000000 08:05 35331                      /usr/lib/libstdc++.so.6.0.8
2aeaa4078000-2aeaa4278000 ---p 000e9000 08:05 35331                      /usr/lib/libstdc++.so.6.0.8
2aeaa4278000-2aeaa427e000 r--p 000e9000 08:05 35331                      /usr/lib/libstdc++.so.6.0.8
2aeaa427e000-2aeaa4281000 rw-p 000ef000 08:05 35331                      /usr/lib/libstdc++.so.6.0.8
2aeaa4281000-2aeaa4293000 rw-p 2aeaa4281000 00:00 0 
2aeaa4293000-2aeaa42a0000 r-xp 00000000 08:05 98318                      /lib/libgcc_s.so.1
2aeaa42a0000-2aeaa44a0000 ---p 0000d000 08:05 98318                      /lib/libgcc_s.so.1
2aeaa44a0000-2aeaa44a1000 rw-p 0000d000 08:05 98318                      /lib/libgcc_s.so.1
2aeaa44a1000-2aeaa44a2000 rw-p 2aeaa44a1000 00:00 0 
2aeaa44a2000-2aeaa45e9000 r-xp 00000000 08:05 98325                      /lib/libc-2.5.so
2aeaa45e9000-2aeaa47e9000 ---p 00147000 08:05 98325                      /lib/libc-2.5.so
2aeaa47e9000-2aeaa47ec000 r--p 00147000 08:05 98325                      /lib/libc-2.5.so
2aeaa47ec000-2aeaa47ee000 rw-p 0014a000 08:05 98325                      /lib/libc-2.5.so
2aeaa47ee000-2aeaa47f3000 rw-p 2aeaa47ee000 00:00 0 
2aeaa47f3000-2aeaa4832000 r-xp 00000000 08:05 202022                     /usr/local/lib64/libosgText.so.2.0.0
2aeaa4832000-2aeaa4a31000 ---p 0003f000 08:05 202022                     /usr/local/lib64/libosgText.so.2.0.0
2aeaa4a31000-2aeaa4a34000 rw-p 0003e000 08:05 202022                     /usr/local/lib64/libosgText.so.2.0.0
2aeaa4a34000-2aeaa4a85000 r-xp 00000000 08:05 202019                     /usr/local/lib64/libosgGA.so.2.0.0
2aeaa4a85000-2aeaa4c85000 ---p 00051000 08:05 202019                     /usr/local/lib64/libosgGA.so.2.0.0
2aeaa4c85000-2aeaa4c8c000 rw-p 00051000 08:05 202019                     /usr/local/lib64/libosgGA.so.2.0.0
2aeaa4c8c000-2aeaa4c8d000 rw-p 2aeaa4c8c000 00:00 0 
2aeaa4c8d000-2aeaa4c8f000 r-xp 00000000 08:05 36861                      /usr/lib/libXau.so.6.0.0
2aeaa4c8f000-2aeaa4e8e000 ---p 00002000 08:05 36861                      /usr/lib/libXau.so.6.0.0
2aeaa4e8e000-2aeaa4e8f000 rw-p 00001000 08:05 36861                      /usr/lib/libXau.so.6.0.0
2aeaa4e8f000-2aeaa4e90000 rw-p 2aeaa4e8f000 00:00 0 
2aeaa4e90000-2aeaa4e95000 r-xp 00000000 08:05 36863                      /usr/lib/libXdmcp.so.6.0.0
2aeaa4e95000-2aeaa5094000 ---p 00005000 08:05 36863                      /usr/lib/libXdmcp.so.6.0.0
2aeaa5094000-2aeaa5095000 rw-p 00004000 08:05 36863                      /usr/lib/libXdmcp.so.6.0.0
2aeaa5095000-2aeaa5098000 rw-p 2aeaa5095000 00:00 0 
2aeaa5098000-2aeaa58e4000 r-xp 00000000 08:05 475907                     /usr/lib/dri/fglrx_dri.so
2aeaa58e4000-2aeaa59e3000 ---p 0084c000 08:05 475907                     /usr/lib/dri/fglrx_dri.so
2aeaa59e3000-2aeaa5adb000 rw-p 0084b000 08:05 475907                     /usr/lib/dri/fglrx_dri.so
2aeaa5adb000-2aeaa5b80000 rw-p 2aeaa5adb000 00:00 0 
2aeaa5b93000-2aeaa5c56000 r-xp 00000000 08:05 36837                      /usr/lib/libstdc++.so.5.0.7
2aeaa5c56000-2aeaa5e55000 ---p 000c3000 08:05 36837                      /usr/lib/libstdc++.so.5.0.7
2aeaa5e55000-2aeaa5e5e000 rw-p 000c2000 08:05 36837                      /usr/lib/libstdc++.so.5.0.7
2aeaa5e5e000-2aeaa5e6f000 rw-p 2aeaa5e5e000 00:00 0 
2aeaa5e6f000-2aeaa5e77000 r-xp 00000000 08:05 98341                      /lib/librt-2.5.so
2aeaa5e77000-2aeaa6076000 ---p 00008000 08:05 98341                      /lib/librt-2.5.so
2aeaa6076000-2aeaa6078000 rw-p 00007000 08:05 98341                      /lib/librt-2.5.so
2aeaa6078000-2aeaae058000 rw-s 00003000 00:0d 18394                      /dev/dri/card0
2aeaae058000-2aeaae05a000 rw-s 00002000 00:0d 18394                      /dev/dri/card0
2aeaae05a000-2aeaae06a000 rw-s 00004000 00:0d 18394                      /dev/dri/card0
2aeaae06a000-2aeaae06b000 rw-s 00005000 00:0d 18394                      /dev/dri/card0
2aeaae06b000-2aeaae16b000 rw-s 00006000 00:0d 18394                      /dev/dri/card0
2aeaae16b000-2aeaae7ab000 rw-s 00007000 00:0d 18394                      /dev/dri/card0
2aeaae7ab000-2aeaae8eb000 rw-s 00070000 00:0d 18394                      /dev/dri/card0
2aeaae8eb000-2aeaae92c000 rw-p 2aeaae8eb000 00:00 0 
2aeaae931000-2aeaae934000 rw-s 00073000 00:0d 18394                      /dev/dri/card0
2aeaae934000-2aeaae93e000 rw-p 2aeaae934000 00:00 0 
2aeaae97a000-2aeaaebaf000 rw-p 2aeaae97a000 00:00 0 
2aeaaebaf000-2aeaaf0af000 rw-s 0000a000 00:0d 18394                      /dev/dri/card0
2aeaaf0af000-2aeaaf5af000 rw-s 0000b000 00:0d 18394                      /dev/dri/card0
2aeaaf5af000-2aeaaf5b1000 rw-p 2aeaaf5af000 00:00 0 
2aeaaf5b9000-2aeaaf5c1000 r-xp 00000000 08:05 688255                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_rgb.so
2aeaaf5c1000-2aeaaf7c0000 ---p 00008000 08:05 688255                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_rgb.so
2aeaaf7c0000-2aeaaf7c1000 rw-p 00007000 08:05 688255                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_rgb.so
2aeaaf7c1000-2aeaaf882000 rw-p 2aeaaf7c1000 00:00 0 
2aeaaf882000-2aeaaf88c000 r-xp 00000000 08:05 688284                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_txf.so
2aeaaf88c000-2aeaafa8b000 ---p 0000a000 08:05 688284                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_txf.so
2aeaafa8b000-2aeaafa8c000 rw-p 00009000 08:05 688284                     /usr/local/lib64/osgPlugins-2.0.0/osgdb_txf.so
2aeaafa8c000-2aeaafa8d000 rw-p 2aeaafa8c000 00:00 0 
2aeaafa8d000-2aeaafb8d000 rw-s 00000000 00:12 32496                      /dev/shm/ATISHM00
2aeaafb8d000-2aeaafba4000 rw-p 2aeaae92c000 00:00 0 
2aeab01a7000-2aeab09a8000 rw-p 2aeab01a7000 00:00 0 
7fff0ae82000-7fff0ae96000 rwxp 7fff0ae82000 00:00 0                      [stack]
7fff0ae96000-7fff0ae98000 rw-p 7fff0ae96000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
Aborted (core dumped)
user@ubuntu:~/myprogs/FlightGear-0.9/source/src/Main$ 


```maybe I try this, just found it in an obscure FG documentation page

> 
Note: If for whatever reason you want to re-build the simulator, use the command make distclean either in the SimGear-X.X.X or in the FlightGear-X.X.X directory to remove all the build. If you want to re-run configure (for instance because of having installed another version of PLIB etc.), remove the files config.cache from these same directories before.
It didn't help

I did find someone else who had problems along the same lines; invalid pointer stuff:

[http://www.opensubscriber.com/message/flightgear-devel@lists.sourceforge.net/5987043.html](http://www.opensubscriber.com/message/flightgear-devel@lists.sourceforge.net/5987043.html)

also i find this at the flightgear site:

> 
[SIZE=-1] FreeGlut 2.4.0 has a critical bug that crashes FlightGear.  If        you plan to use FreeGlut instead of SDL you will need to        downgrade to 2.2.0 or run the CVS version of FreeGlut.[/SIZE]
I look in synaptic, and what do I have? [SIZE=-1] FreeGlut 2.4.0; that's got to be worth looking into eh. At a brief glance though, removing FreeGlut 2.4.0 via synaptic seems to involve removing flightgear, osg, and a slew of other stuff.. nasty.... is there a less drastic way of downgrading FreeGlut or is this the point where I might as well bit the bullet & do that complete reload 

also I believe there's a >make uninstall< command.. possibly useful to help reinstalling just FG if I can avoid a system reload!

Enough for tonight.


--------------------------------------


Good morning..

Potentially useful page:
[http://www.jp.flightgear.org/Docs/InstallGuide/getstartch2.html](http://www.jp.flightgear.org/Docs/InstallGuide/getstartch2.html)

I have removed freeglut 2.4.0 via synaptic

It has removed the following (apparrently)

glut-doc
glutg3-dev
plib1.8.4-dev
ubuntu-desktop
flightgear
freeglut3-dev
glut-doc
glutg3
glutg3-dev
libglut3
openscenegraph
plib1.8.4c2

There's a freeglut 2.2.0 here --> [http://freeglut.sourceforge.net/](http://freeglut.sourceforge.net/)
linked to by flightgear so hopefully ok
[/SIZE]

---

### Post by ecs_pf5 on 2007-06-21
Try as I might, can't get freeglut 2.2.0 past 'make':

```

user@ubuntu:~$ cd /home/user/myprogs/freeglut-2.2.0
user@ubuntu:~/myprogs/freeglut-2.2.0$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for working const... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for executable suffix... no
checking how to run the C preprocessor... gcc -E
checking host system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for object suffix... o
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for X... libraries , headers 
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XF86VidModeSwitchToMode in -lXxf86vm... yes
checking for ANSI C header files... yes
checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glx.h... yes
checking for X11/extensions/xf86vmode.h... yes
checking for main in -lm... yes
updating cache ./config.cache
creating ./config.status
creating Makefile
creating doc/Makefile
creating progs/Makefile
creating progs/demos/Makefile
creating progs/demos/CallbackMaker/Makefile
creating progs/demos/Fractals/Makefile
creating progs/demos/Fractals_random/Makefile
creating progs/demos/Lorenz/Makefile
creating progs/demos/One/Makefile
creating progs/demos/shapes/Makefile
creating src/Makefile
creating include/Makefile
creating include/GL/Makefile
creating config.h
user@ubuntu:~/myprogs/freeglut-2.2.0$ 


user@ubuntu:~/myprogs/freeglut-2.2.0$ make
make  all-recursive
make[1]: Entering directory `/home/user/myprogs/freeglut-2.2.0'
Making all in src
make[2]: Entering directory `/home/user/myprogs/freeglut-2.2.0/src'
source='freeglut_callbacks.c' object='libglut_la-freeglut_callbacks.lo' libtool=yes \
        depfile='.deps/libglut_la-freeglut_callbacks.Plo' tmpdepfile='.deps/libglut_la-freeglut_callbacks.TPlo' \
        depmode=gcc3 /bin/sh ../depcomp \
        /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c -o libglut_la-freeglut_callbacks.lo `test -f freeglut_callbacks.c || echo './'`freeglut_callbacks.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -c freeglut_callbacks.c -MT libglut_la-freeglut_callbacks.lo -MD -MP -MF .deps/libglut_la-freeglut_callbacks.TPlo  -fPIC -DPIC -o .libs/libglut_la-freeglut_callbacks.lo
freeglut_callbacks.c: In function 'glutDisplayFunc':
freeglut_callbacks.c:54: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutReshapeFunc':
freeglut_callbacks.c:63: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutKeyboardFunc':
freeglut_callbacks.c:72: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutSpecialFunc':
freeglut_callbacks.c:80: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutVisibilityFunc':
freeglut_callbacks.c:143: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutKeyboardUpFunc':
freeglut_callbacks.c:157: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutSpecialUpFunc':
freeglut_callbacks.c:165: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutJoystickFunc':
freeglut_callbacks.c:175: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutMouseFunc':
freeglut_callbacks.c:190: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutMouseWheelFunc':
freeglut_callbacks.c:198: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutMotionFunc':
freeglut_callbacks.c:207: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutPassiveMotionFunc':
freeglut_callbacks.c:216: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutEntryFunc':
freeglut_callbacks.c:224: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutCloseFunc':
freeglut_callbacks.c:232: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutOverlayDisplayFunc':
freeglut_callbacks.c:270: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutWindowStatusFunc':
freeglut_callbacks.c:278: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutSpaceballMotionFunc':
freeglut_callbacks.c:286: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutSpaceballRotateFunc':
freeglut_callbacks.c:294: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutSpaceballButtonFunc':
freeglut_callbacks.c:302: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutButtonBoxFunc':
freeglut_callbacks.c:310: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutDialsFunc':
freeglut_callbacks.c:318: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutTabletMotionFunc':
freeglut_callbacks.c:326: error: invalid lvalue in assignment
freeglut_callbacks.c: In function 'glutTabletButtonFunc':
freeglut_callbacks.c:334: error: invalid lvalue in assignment
make[2]: *** [libglut_la-freeglut_callbacks.lo] Error 1
make[2]: Leaving directory `/home/user/myprogs/freeglut-2.2.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/myprogs/freeglut-2.2.0'
make: *** [all] Error 2
user@ubuntu:~/myprogs/freeglut-2.2.0$ 

```


some dependencies I'm missing?

---

### Post by SlowButDim on 2007-06-21
I found this from [http://wiki.flightgear.org/flightgear_wiki/index.php?title=OpenSUSE_10.1_10.2](http://wiki.flightgear.org/flightgear_wiki/index.php?title=OpenSUSE_10.1_10.2) :

> D) There are actually 2 FlightGear CVS branches - PLIB and OSG. Although OSG is FlightGears graphic system for the future, it is still under development, lacking some important features, actually (Febr. 07) working bad on my PC and a little more difficult to compile. This is why I am only reporting about building the PLIB FlightGear system. Once you are familiar with the building process, it should be no problem to build a separate (parallel) OSG system on your PC. Have a look on this wiki for further information.

So may be it is not a good idea to build with OSG after all? That page may help you....

You have started with the hard one :)

---

### Post by ecs_pf5 on 2007-06-21
Yes perhaps you're right. I am persevering with it because it seems to be nearly working.. if I can just get freeglut 2.2.0 instead of 2.4.0 installed, I'm hoping that magically everything will be alright then :lol:

Also I'm not too worried by the difficulty, if one doesn't try difficult things, one never progresses

But if it still doesn't work, yes I will go back and try the plib way.. someone commented along similar lines a while ago at the flightgear forum.

Just feels like the OSG build is so very near at the moment.

I tried the 'nightly cvs tarball' of freeglut; (trying to go the opposite way i.e. the very latest, to get away from this reported bug in 2.4.0) can't get that one to build either, at the mo :(

```

root@ubuntu:/home/user/myprogs/freeglutcvs# ./autogen.sh
Generating build information using aclocal, automake and autoconf
This may take a while ...
/usr/share/aclocal/lib3ds.m4:4: warning: underquoted definition of AM_PATH_LIB3DS
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
Now you are ready to run ./configure
root@ubuntu:/home/user/myprogs/freeglutcvs# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for an ANSI C-conforming const... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XF86VidModeSwitchToMode in -lXxf86vm... yes
checking for ANSI C header files... (cached) yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking GL/glx.h usability... yes
checking GL/glx.h presence... yes
checking for GL/glx.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for X11/extensions/xf86vmode.h... yes
checking whether gcc needs -traditional... no
checking for vprintf... yes
checking for _doprnt... no
checking for cos in -lm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating include/GL/Makefile
config.status: creating include/Makefile
config.status: creating progs/Makefile
config.status: creating progs/demos/CallbackMaker/Makefile
config.status: creating progs/demos/Fractals/Makefile
config.status: creating progs/demos/Fractals_random/Makefile
config.status: creating progs/demos/Lorenz/Makefile
config.status: creating progs/demos/Makefile
config.status: creating progs/demos/One/Makefile
config.status: creating progs/demos/shapes/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@ubuntu:/home/user/myprogs/freeglutcvs# make
make  all-recursive
make[1]: Entering directory `/home/user/.Trash/freeglutcvs'
Making all in src
make[2]: Entering directory `/home/user/.Trash/freeglutcvs/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include    -g -O2 -Wall -pedantic -Werror -MT libglut_la-freeglut_callbacks.lo -MD -MP -MF ".deps/libglut_la-freeglut_callbacks.Tpo" -c -o libglut_la-freeglut_callbacks.lo `test -f 'freeglut_callbacks.c' || echo './'`freeglut_callbacks.c; \
        then mv -f ".deps/libglut_la-freeglut_callbacks.Tpo" ".deps/libglut_la-freeglut_callbacks.Plo"; else rm -f ".deps/libglut_la-freeglut_callbacks.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -g -O2 -Wall -pedantic -Werror -MT libglut_la-freeglut_callbacks.lo -MD -MP -MF .deps/libglut_la-freeglut_callbacks.Tpo -c freeglut_callbacks.c  -fPIC -DPIC -o .libs/libglut_la-freeglut_callbacks.o
cc1: warnings being treated as errors
freeglut_callbacks.c: In function 'glutDisplayFunc':
freeglut_callbacks.c:50: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:50: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutReshapeFunc':
freeglut_callbacks.c:59: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:59: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutKeyboardFunc':
freeglut_callbacks.c:69: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:69: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutSpecialFunc':
freeglut_callbacks.c:78: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:78: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'fghVisibility':
freeglut_callbacks.c:135: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:135: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c: In function 'glutVisibilityFunc':
freeglut_callbacks.c:141: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:141: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutKeyboardUpFunc':
freeglut_callbacks.c:156: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:156: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutSpecialUpFunc':
freeglut_callbacks.c:165: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:165: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutJoystickFunc':
freeglut_callbacks.c:178: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:178: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutMouseFunc':
freeglut_callbacks.c:194: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:194: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutMouseWheelFunc':
freeglut_callbacks.c:203: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:203: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutMotionFunc':
freeglut_callbacks.c:213: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:213: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutPassiveMotionFunc':
freeglut_callbacks.c:223: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:223: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutEntryFunc':
freeglut_callbacks.c:232: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:232: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutCloseFunc':
freeglut_callbacks.c:241: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:241: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutOverlayDisplayFunc':
freeglut_callbacks.c:282: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:282: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutWindowStatusFunc':
freeglut_callbacks.c:291: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:291: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutSpaceballMotionFunc':
freeglut_callbacks.c:300: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:300: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutSpaceballRotateFunc':
freeglut_callbacks.c:309: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:309: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutSpaceballButtonFunc':
freeglut_callbacks.c:318: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:318: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutButtonBoxFunc':
freeglut_callbacks.c:327: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:327: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutDialsFunc':
freeglut_callbacks.c:336: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:336: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutTabletMotionFunc':
freeglut_callbacks.c:345: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:345: warning: ISO C forbids conversion of function pointer to object pointer type
freeglut_callbacks.c: In function 'glutTabletButtonFunc':
freeglut_callbacks.c:354: warning: ISO C forbids conversion of object pointer to function pointer type
freeglut_callbacks.c:354: warning: ISO C forbids conversion of function pointer to object pointer type
make[2]: *** [libglut_la-freeglut_callbacks.lo] Error 1
make[2]: Leaving directory `/home/user/.Trash/freeglutcvs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/.Trash/freeglutcvs'
make: *** [all] Error 2
root@ubuntu:/home/user/myprogs/freeglutcvs# 


```
Thanks for the opensuse page - looks very helpful


Giving that a good close read..

---

### Post by SlowButDim on 2007-06-21
I managed to compile it, with OSG (I think)

I'm little bit confused. It seems that OSG is now default... 

Here is what I did:
1. compile and install OSG 2.0 (stable)
2. install Plib dev-package from apt (```
sudo apt-get install plib1.8.4-dev
```)
3. compile and install simgear from cvs ([http://www.simgear.org/cvs.html](http://www.simgear.org/cvs.html))
4. compile FG from cvs ([http://www.flightgear.org/cvs/anoncvs.html](http://www.flightgear.org/cvs/anoncvs.html))

5. ```
export LD_LIBRARY_PATH=/usr/local/lib
```
6. symlink FlighGear/data to /usr/local/share/FlightGear OR start FG with --fg-root=/WHERE/YOUR/DATA/IS

Everything can be compiled with defaults. I think that one could set the path to data directory when configuring FG but I didn't now what option I should have used so I took the easy way (symlink).

So I *think* this is now using osg but I'm not sure :D

EDIT: Wish I knew how to fly with these things!

---

### Post by ecs_pf5 on 2007-06-21
:cool: Well done \\:D/

Bogged down with attending to an email problem at the mo but I'll try running through that way ASAP

Nice one!

[edit]

are you on 64 or 32 bit?

Done my Feisty 7.04 x64 reinstall now

Just completed building OSG2 - the cow is smooth and spins fast now, it was a bit slow and jerky before by comparison.

So something's improved on my setup by the reinstall..

sudo apt-get install plib1.8.4-dev seemed to go just fine

Hmm. Having trouble building simgear, it's demanding openal which I tried to install with sudo aptitude install libopenal0a, it seems to complete but simgear still complains about the lack of  openal:

```

.
.
.
checking for library containing glNewList... -lGL
checking for library containing gluLookAt... -lGLU
checking for library containing glutGetModifiers... -lglut
checking for library containing alGenBuffers... no
checking for library containing alutInit... no

You *must* have the openal library installed on your system to build
SimGear!

Please see README.OpenAL for more details.

configure aborted.

```README.OpenAL:

```

[This file is mirrored in both the FlightGear and SimGear packages.]

You *must* have the development components of OpenAL installed on your system
to build FlightGear!"  You can get a copy here:

    http://www.openal.org

Build notes:

The OpenAL developers do not make "versioned" releases so we recommend that
you pull the latest version via anonymous CVS (follow the instructions at
the OpenAL web site) and build/install that.

```Did that, no joy.. the feb 11 '06 tar.gz failed to compile (& didn't seem to mention dev package anyway) & I couldn't seem to find a cvs download there. So, currently hunting the 'net..

next port of call for libopenal-dev_0.0.8-3_amd64.deb one-click deb installer for Feisty [CLICKY]("http://packages.ubuntu.com/feisty/libdevel/libopenal-dev")

ok that worked, got far further on, but it still fell over at:

```

In file included from ../../simgear/sound/soundmgr_openal.hxx:53,
                 from visual_enviro.cxx:33:
../../simgear/[COLOR=black]sound/s[/COLOR]ample_openal.hxx:52:22: error: AL/alut.h: No such file or directory

```

I guess I need libalut-dev_1.0.1-1_amd64.deb one-click deb installer for Feisty now [CLICKY]("http://packages.ubuntu.com/feisty/libdevel/libalut-dev")

all good, cvs SimGear now successfully make installed

---

### Post by ecs_pf5 on 2007-06-22
Flightgear builds great & starts up successfully, following in your tracks there :p

Now I guess it needs fine tuning. Frame rates are painfully slow here, sufficiently to lock up the entire machine & neccessitate a restart.

```

user@ubuntu:~$ cd /builds/FlightGear/source/src/Main
user@ubuntu:/builds/FlightGear/source/src/Main$ fgfs --fg-root=/builds/FlightGear/data
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
Warning: detected OpenGL error 'invalid enumerant' after RenderBin::draw(,)
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.18 2007-01-15 12:50:45 ehofman Exp $
  Description:   Cessna C-172
Warning: detected OpenGL error 'invalid value' after RenderBin::draw(,) - thousands of instances
Initializing Nasal Electrical System
Warning: detected OpenGL error 'invalid value' after RenderBin::draw(,) - thousands of instances
power up
Warning: detected OpenGL error 'invalid value' after RenderBin::draw(,) - thousands of instances
freeglut  ERROR:  Function <glutSetCursor> called without first calling 'glutInit'.

```Note that that final line wasn't a fatal error; I kept the FG window small & that allowed it to at least continue running without crashing the PC, until I explicitly stopped it myself.

The OSG cow, on the other hand, runs like a dream. It does give one single console error but it doesn't seem to affect it's performance in any way:

```

user@ubuntu:~$ osgviewer cow.osg
Warning: detected OpenGL error 'invalid enumerant' after RenderBin::draw(,)
user@ubuntu:~$ 

```You don't notice there's been an error until you hit esc then look at the terminal window.

Time to scratch head again :lol:


> 
You'll also need OpenGL-headers. If you are using Nvidia drivers from Ubuntu repository, then
    sudo apt-get install nvidia-glx-dev 


I have an ATI Radeon X700 video card, using the fglrx drivers - so I skipped the above & hoped for the best.

That's a likely cause of the detected OpenGL errors? Damn ATI :x

Tried "ati", "fglrx", and "radeon" drivers in xorg.conf; tried ensuring Composite was "False" in xorg.conf, also AIGLX "off", no difference:

```

user@ubuntu:~$ glxgears
987 frames in 6.2 seconds = 159.518 FPS
241 frames in 7.4 seconds = 32.426 FPS
240 frames in 7.4 seconds = 32.285 FPS
240 frames in 7.5 seconds = 32.177 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
user@ubuntu:~$ glxinfo | grep direct 
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
user@ubuntu:~$ 

```

I asked also at the FlightGear forum:

[http://www.flightgear.org/forums/viewtopic.php?p=1311#1311](http://www.flightgear.org/forums/viewtopic.php?p=1311#1311)

What's the frame rates like on your build? does it seem to run relatively smoothly on your machine?

---

### Post by SlowButDim on 2007-06-24
ATI's drivers has a very bad reputation in Linux-world :(

I receive only this error when running FG:
```

 freeglut  ERROR:  Function <glutSetCursor> called without first calling 'glutInit'.
```

Frame rates are 55 -75 with default settings. It runs OK but there are some little "freeze" moments (takes a fraction of a second). I have Nvidia Geforce 6800.

---

### Post by bertrandperrier on 2007-07-04
i have the same problem
with a Nvidia GeForce TI4200 
please help me

---

