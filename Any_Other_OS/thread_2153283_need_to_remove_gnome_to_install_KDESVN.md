---
title: "need to remove gnome to install KDESVN?"
date: 2013-06-10
forum: Any Other OS
---

### Post by mrmaxpires on 2013-06-10
Hi guys, this is my first post here and I'm having problems to install the KDEsvn. 
I'm kind of new in linux systems, so I'm sure that a lot problems I have is just ignorance. 
by aptitude command it returns:

 starOne:/home/maxp# aptitude install kdesvnThe following NEW packages will be installed:
  hal{a} hal-info{a} kaboom{a} kdebase-runtime{a} kdebase-runtime-data{a} kdelibs-bin{a} kdelibs5-data{a} kdelibs5-plugins{a} kdesvn 
  kdesvn-kio-plugins{a} kdoctools{a} kompare{a} libaacplus2{ab} libattica0{a} libavcodec54{ab} libavutil51{ab} libclucene0ldbl{a} libfame-0.9-1{ab} 
  libfdk-aac0{ab} libiodbc2{a} libiso9660-7{a} libkde3support4{a} libkdecore5{a} libkdesu5{a} libkdeui5{a} libkdnssd4{a} libkfile4{a} libkhtml5{a} 
  libkio5{a} libkjsapi4{a} libkjsembed4{a} libkmediaplayer4{a} libknewstuff2-4{a} libknewstuff3-4{a} libknotifyconfig4{a} libkntlm4{a} libkparts4{a} 
  libkpty4{a} libkrosscore4{a} libktexteditor4{a} libkutils4{a} libnepomuk4{a} libnepomukquery4a{a} libplasma3{a} libpolkit-qt-1-0{a} libpostproc52{ab} 
  libsolid4{a} libsoprano4{a} libstreamanalyzer0{a} libstreams0{a} libsvnqt6{a} libthreadweaver4{a} libvcdinfo0{a} libvirtodbc0{a} libx264-130{ab} 
  libxcb-shape0{a} libxcb-shm0{a} libxcb-xv0{a} libxine1{a} libxine1-bin{a} libxine1-ffmpeg{a} libxine1-misc-plugins{ab} libxine1-plugins{a} 
  libxine1-x{a} odbcinst{a} odbcinst1debian2{a} oxygen-icon-theme{a} phonon-backend-xine{a} plasma-scriptengine-javascript{a} 
  shared-desktop-ontologies{a} soprano-daemon{a} virtuoso-minimal{a} virtuoso-opensource-6.1-bin{a} virtuoso-opensource-6.1-common{a} 
The following packages will be upgraded:
  libmp3lame0{b} 
1 packages upgraded, 74 newly installed, 0 to remove and 191 not upgraded.
Need to get 69.1 MB of archives. After unpacking 179 MB will be used.
The following packages have unmet dependencies:
  libavutil51: PreDepends: multiarch-support which is a virtual package.
  libx264-130: PreDepends: multiarch-support which is a virtual package.
  libxine1-misc-plugins: Depends: libbluray1 which is a virtual package.
                         Depends: libcdio13 (>= 0.83) which is a virtual package.
                         Depends: libiso9660-8 (>= 0.83) which is a virtual package.
                         Depends: libpulse0 (>= 0.99.1) but 0.9.21-3+squeeze1 is installed.
  libpostproc52: PreDepends: multiarch-support which is a virtual package.
  libfame-0.9-1: PreDepends: multiarch-support which is a virtual package.
  libmp3lame0: PreDepends: multiarch-support which is a virtual package.
  libfdk-aac0: PreDepends: multiarch-support which is a virtual package.
  libavcodec54: Depends: libcrystalhd3 which is a virtual package.
                Depends: libopus0 which is a virtual package.
                Depends: libva1 (> 1.0.15~) but 1.0.7-0.0 is installed.
                Depends: libvo-aacenc0 which is a virtual package.
                Depends: libvo-amrwbenc0 which is a virtual package.
                Depends: libvpx1 (>= 1.0.0) which is a virtual package.
                PreDepends: multiarch-support which is a virtual package.
  libaacplus2: PreDepends: multiarch-support which is a virtual package.
The following actions will resolve these dependencies:


      Remove the following packages:                          
1)      acidrip                                               
2)      browser-plugin-gnash                                  
3)      ffmpeg                                                
4)      gnash                                                 
5)      gnash-common                                          
6)      gnome                                                 
7)      gstreamer0.10-ffmpeg                                  
8)      libavcodec52                                          
9)      libavdevice52                                         
10)     libavfilter1                                          
11)     libavformat52                                         
12)     libmp3lame0                                           
13)     libqmmp-misc                                          
14)     mencoder                                              
15)     mplayer                                               
16)     qmmp                                                  
17)     qmmp-skins-pack                                       


      Keep the following packages at their current version:   
18)     kdebase-runtime [Not Installed]                       
19)     kdesvn [Not Installed]                                
20)     kompare [Not Installed]                               
21)     libaacplus2 [Not Installed]                           
22)     libavcodec54 [Not Installed]                          
23)     libavutil51 [Not Installed]                           
24)     libfame-0.9-1 [Not Installed]                         
25)     libfdk-aac0 [Not Installed]                           
26)     libpostproc52 [Not Installed]                         
27)     libx264-130 [Not Installed]                           
28)     libxine1 [Not Installed]                              
29)     libxine1-ffmpeg [Not Installed]                       
30)     libxine1-misc-plugins [Not Installed]                 
31)     libxine1-plugins [Not Installed]                      
32)     libxine1-x [Not Installed]                            
33)     phonon-backend-xine [Not Installed]                   


      Leave the following dependencies unresolved:            
34)     kdelibs5-plugins recommends kdebase-runtime (>= 4:4.4)
35)     kdesvn recommends kompare                             
36)     gnome recommends mozilla-plugin-gnash                 
37)     mplayer-skin-blue recommends mplayer                  
38)     totem recommends gstreamer0.10-ffmpeg                 
39)     libxine1 recommends libxine1-ffmpeg                   




Accept this solution? [Y/n/q/?]

uname -a
Linux starOne 2.6.32-5-686 #1 SMP Sun Sep 23 09:49:36 UTC 2012 i686 GNU/Linux


any help will be appreciated.

BR
Max

---

### Post by mips on 2013-06-10
You are better off starting with a netinstall. It's easier building up from the ground than removing stuff.

---

