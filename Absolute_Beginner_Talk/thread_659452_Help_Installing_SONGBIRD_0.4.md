---
title: "Help Installing SONGBIRD 0.4"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by SiCkGODV3 on 2008-01-05
ok i download songbird 0.3.whatever doing the script thing..........i can install a .deb file coz all u have to do is click on it but when i down load the new songbird it is a .tar.gz type file and when i extract it after downloading it to my desktop.........i go into termanal and do this..............
sickgodv3@Linux-1:~$ sudo su
[sudo] password for sickgodv3:
root@Linux-1:/home/sickgodv3# cd /home/sickgodv3/Desktop/Songbird
root@Linux-1:/home/sickgodv3/Desktop/Songbird# ./configure
bash: ./configure: No such file or directory
............WTF.........i know i didnt spell it wrong coz i draged it in the termanl then deleted the "...."............can someone post a link to install songbird 0.4 in a .deb type or tell me what is wrong i have looked on help sites of how to install a tar.gz but when i put in ./configure it says "No such file or directory" PLZ HELP

---

### Post by voteforpedro36 on 2008-01-05
Instead of ./configure, try running ./songbird

It doesn't need any install, just to be ran,

---

### Post by sub2007 on 2008-01-05
This link should help: [http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

In more detail, it's returning an error because there is no configure file in that archive: ./configure only works if there is a configure file. Not all .tar.gz's require compiling - some are already precompiled and so all that is required is to drop the extracted folder in a convenient location and then run the executable within the folder 

Nearly all .tar.gz's come with a readme or install guide. I always read that before starting an installation - it's not always helpful but it usually is.

---

### Post by flehnerz on 2008-02-09
This is what I got, absolutely nothing

```
frank@frank-laptop:~$ cd ~/Desktop/Songbird
frank@frank-laptop:~/Desktop/Songbird$ ./instal
bash: ./instal: No such file or directory
frank@frank-laptop:~/Desktop/Songbird$ ./install
bash: ./install: No such file or directory
frank@frank-laptop:~/Desktop/Songbird$ ./songbird
doEULA
doFirstRun
doMainwinStart
*** glibc detected *** ./songbird: realloc(): invalid next size: 0x08c596f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d44b0c]
/lib/tls/i686/cmov/libc.so.6(realloc+0x106)[0xb7d46a66]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb77a2177]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb77a27a0]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb77a297b]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb77a2d8e]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb6f67f05]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb6f66e2c]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb6f6822b]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb774d34a]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb6f68123]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb6f6776a]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb6f581d0]
/home/frank/Desktop/Songbird/components/sbMetadataHandlerTaglib.so[0xaea80755]
/home/frank/Desktop/Songbird/components/sbMetadataManager.so(_ZN13sbMetadataJob19StartHandlerForItemEPNS_9jobitem_tE+0xfe)[0xb03610aa]
/home/frank/Desktop/Songbird/components/sbMetadataManager.so(_ZN13sbMetadataJob18RunThreadBatchFuncEP11nsISupports+0x185)[0xb03620ed]
/home/frank/Desktop/Songbird/components/sbMetadataManager.so[0xb0362eea]
/home/frank/Desktop/Songbird/components/sbLocalDatabaseLibrary.so[0xb4879fd2]
/home/frank/Desktop/Songbird/components/sbLocalDatabaseLibrary.so[0xb4874837]
/home/frank/Desktop/Songbird/components/sbMetadataManager.so(_ZN13sbMetadataJob9RunThreadEPi+0x18b)[0xb03608db]
/home/frank/Desktop/Songbird/components/sbMetadataManager.so[0xb03640da]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb7788809]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb7753110]
/home/frank/Desktop/Songbird/xulrunner/libxul.so[0xb7788658]
/home/frank/Desktop/Songbird/xulrunner/libnspr4.so[0xb7ccc82f]
/lib/tls/i686/cmov/libpthread.so.0[0xb7f5046b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7dac6de]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:03 38747      /home/frank/Desktop/Songbird/songbird
0804f000-08050000 rw-p 00006000 08:03 38747      /home/frank/Desktop/Songbird/songbird
08050000-08c6b000 rw-p 08050000 00:00 0          [heap]
aea47000-aead2000 r-xp 00000000 08:03 38698      /home/frank/Desktop/Songbird/components/sbMetadataHandlerTaglib.so
aead2000-aead6000 rw-p 0008a000 08:03 38698      /home/frank/Desktop/Songbird/components/sbMetadataHandlerTaglib.so
aead6000-aeadd000 r-xp 00000000 08:03 361270     /usr/lib/libfam.so.0.0.0
aeadd000-aeade000 rw-p 00006000 08:03 361270     /usr/lib/libfam.so.0.0.0
aeade000-aeae4000 r-xp 00000000 08:03 1504410    /lib/libacl.so.1.1.0
aeae4000-aeae5000 rw-p 00005000 08:03 1504410    /lib/libacl.so.1.1.0
aeae5000-aeae8000 r-xp 00000000 08:03 1504416    /lib/libattr.so.1.1.0
aeae8000-aeae9000 rw-p 00002000 08:03 1504416    /lib/libattr.so.1.1.0
aeafc000-aeb08000 r-xp 00000000 08:03 425511     /usr/lib/gnome-vfs-2.0/modules/libfile.so
aeb08000-aeb09000 rw-p 0000b000 08:03 425511     /usr/lib/gnome-vfs-2.0/modules/libfile.so
aeb09000-aeb1d000 rw-p aeb09000 00:00 0 
aeb1d000-aeb27000 r-xp 00000000 08:03 38720      /home/frank/Desktop/Songbird/components/sbIntegration.so
aeb27000-aeb28000 rw-p 0000a000 08:03 38720      /home/frank/Desktop/Songbird/components/sbIntegration.so
aeb28000-aeb38000 rw-p aeb28000 00:00 0 
aeb38000-aeb39000 ---p aeb38000 00:00 0 
aeb39000-af339000 rw-p aeb39000 00:00 0 
af339000-af33a000 ---p af339000 00:00 0 
af33a000-afb3a000 rw-p af33a000 00:00 0 
afb3a000-afb3b000 ---p afb3a000 00:00 0 
afb3b000-b033b000 rw-p afb3b000 00:00 0 
b033b000-b037e000 r-xp 00000000 08:03 38696      /home/frank/Desktop/Songbird/components/sbMetadataManager.so
b037e000-b0380000 rw-p 00042000 08:03 38696      /home/frank/Desktop/Songbird/components/sbMetadataManager.so
b0380000-b0384000 rw-p b0380000 00:00 0 
b0384000-b0386000 r-xp 00000000 08:03 508196     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b0386000-b0387000 rw-p 00001000 08:03 508196     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b0387000-b03c4000 r--p 00000000 08:03 590033     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b03c4000-b03c8000 rw-p b03c4000 00:00 0 
b03c8000-b03cf000 r-xp 00000000 08:03 38675      /home/frank/Desktop/Songbird/components/sbMediaSniffer.so
b03cf000-b03d0000 rw-p 00007000 08:03 38675      /home/frank/Desktop/Songbird/components/sbMediaSniffer.so
b03d0000-b0408000 r-xp 00000000 08:03 50465      /home/frank/Desktop/Songbird/xulrunner/libnssckbi.so
b0408000-b0412000 rw-p 00038000 08:03 50465      /home/frank/Desktop/Songbird/xulrunner/libnssckbi.so
b0412000-b045c000 r-xp 00000000 08:03 50461      /home/frank/Desktop/Songbird/xulrunner/libfreebl3.so
b045c000-b045e000 rw-p 00049000 08:03 50461      /home/frank/Desktop/Songbird/xulrunner/libfreebl3.so
b045e000-b0484000 r-xp 00000000 08:03 50466      /home/frank/Desktop/Songbird/xulrunner/libnssdbm3.so
b0484000-b0487000 rw-p 00026000 08:03 50466      /home/frank/Desktop/Songbird/xulrunner/libnssdbm3.so
b0487000-b0488000 ---p b0487000 00:00 0 
b0488000-b0c88000 rw-p b0488000 00:00 0 
b0c88000-b0c89000 ---p b0c88000 00:00 0 
b0c89000-b1499000 rw-p b0c89000 00:00 0 
b1499000-b149a000 ---p b1499000 00:00 0 
b149a000-b1c9a000 rw-p b149a000 00:00 0 
b1c9a000-b1cfa000 rw-s 00000000 00:09 1933325    /SYSV00000000 (deleted)
b1cfa000-b1d00000 r-xp 00000000 08:03 425599     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b1d00000-b1d01000 rw-p 00005000 08:03 425599     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b1d02000-b1d05000 r--s 00000000 08:03 903879     /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b1d05000-b1d07000 r--s 00000000 08:03 903878     /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b1d07000-b1d0d000 r--s 00000000 08:03 903877     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b1d0d000-b1d10000 r--s 00000000 08:03 903875     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b1d10000-b1d13000 r--s 00000000 08:03 903874     /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b1d13000-b1d14000 r--s 00000000 08:03 903868     /var/cache/fontconfig/1b70ff56935fd37e75520e134628df26-x86.cache-2
b1d14000-b1d15000 r--s 00000000 08:03 903867     /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b1d15000-b1d19000 r--s 00000000 08:03 903866     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b1d19000-b1d1a000 r--s 00000000 08:03 903865     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b1d1a000-b1d35000 r--s 00000000 08:03 903864     /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b1d35000-b1d51000 r--s 00000000 08:03 903863     /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b1d51000-b1d6f000 r--s 00000000 08:03 903854     /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b1d6f000-b1d70000 r--s 00000000 08:03 903853     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b1d70000-b1d73000 r--s 00000000 08:03 903852     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b1d73000-b1d74000 r--s 00000000 08:03 903851     /var/cache/fontconfig/7ee55724f82591cb35c3d9771e9e69ed-x86.cache-2
b1d74000-b1d77000 r--s 00000000 08:03 903850     /var/cache/fontconfig/f680583fed5bdc90d95a16af47e16528-x86.cache-2
b1d77000-b1d78000 r--s 00000000 08:03 903849     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b1d78000-b1d79000 r--s 00000000 08:03 903848     /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b1d79000-b1d7a000 r--s 00000000 08:03 903847     /var/cache/fontconfig/5a86461592e14be7c82e45729474f230-x86.cache-2
b1d7a000-b1d80000 r--s 00000000 08:03 903839     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b1d80000-b1d82000 r--s 00000000 08:03 903838     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b1d82000-b1d8a000 r--s 00000000 08:03 903837     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b1d8a000-b1d90000 r--s 00000000 08:03 903836     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b1d90000-b1d91000 r--s 00000000 08:03 903835     /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86.cache-2
b1d91000-b1d92000 r--s 00000000 08:03 903834     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b1d92000-b1da9000 r--s 00000000 08:03 903833     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b1da9000-b1dac000 r--s 00000000 08:03 903832     /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-x86.cache-2
b1dac000-b1dae000 r--s 00000000 08:03 903830     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b1dae000-b1db4000 r--s 00000000 08:03 903829     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b1db4000-b1db5000 r--s 00000000 08:03 903828     /var/cache/fontconfig/ae26c1aac6606cb24499bf89ff8f20df-x86.cache-2
b1db5000-b1db9000 r--s 00000000 08:03 903827     /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b1db9000-b1dbd000 r--s 00000000 08:03 903826     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b1dbd000-b1dc4000 r--s 00000000 08:03 903821     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b1dc4000-b1dc5000 r--s 00000000 08:03 904285     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b1dc5000-b1dc6000 r--s 00000000 08:03 904214     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b1dc6000-b1dc7000 r--s 00000000 08:03 904212     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b1dc7000-b1dcb000 r--s 00000000 08:03 904209     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b1dcb000-b1dd3000 r--s 00000000 08:03 904208     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b1dd3000-b1dd8000 r--s 00000000 08:03 904046     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b1dd8000-b1dde000 r--s 00000000 08:03 904044     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b1dde000-b1de5000 r--s 00000000 08:03 904017     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b1de5000-b1de9000 r--s 00000000 08:03 903932     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b1de9000-b1def000 r--s 00000000 08:03 903930     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b1def000-b1df9000 r--s 00000000 08:03 903928     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b1df9000-b1e00000 r--s 00000000 08:03 903925     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b1e00000-b1e35000 r-xp 00000000 08:03 38705      /home/frank/Desktop/Songbird/components/sbDownloadDevice.so
b1e35000-b1e37000 rw-p 00034000 08:03 38705      /home/frank/Desktop/Songbird/components/sbDownloadDevice.so
b1e37000-b1e42000 r-xp 00000000 08:03 361514     /usr/lib/libhal.so.1.0.0
b1e42000-b1e43000 rw-p 0000b000 08:03 361514     /usr/lib/libhal.so.1.0.0
b1e43000-b1e46000 r--s 00000000 08:03 904210     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b1e46000-b1e48000 r--s 00000000 08:03 904131     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b1e48000-b1e4c000 r--s 00000000 08:03 903922     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b1e4c000-b1e51000 r--s 00000000 08:03 903921     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b1e51000-b1e52000 r--s 00000000 08:03 903825     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b1e52000-b1e56000 rw-p b1e52000 00:00 0 
b1e56000-b1ec3000 r-xp 00000000 08:03 1226699    /home/frank/.songbird1/0bw1npr4.default/extensions/ipod@songbirdnest.com/libraries/sbIPodDevice.so
b1ec3000-b1ec5000 rw-p 0006d000 08:03 1226699    /home/frank/.songbird1/0bw1npr4.default/extensions/ipod@songbirdnest.com/libraries/sbIPodDevice.so
b1ec5000-b1eec000 r-xp 00000000 08:03 1226698    /home/frank/.songbird1/0bw1npr4.default/extensions/ipod@songbirdnest.com/libraries/libgpod.so
b1eec000-b1eee000 rw-p 00026000 08:03 1226698    /home/frank/.songbird1/0bw1npr4.default/extensions/ipod@songbirdnest.com/libraries/libgpod.so
b1eee000-b1ef1000 r-xp 00000000 08:03 16529      /home/frank/.songbird1/0bw1npr4.default/extensions/ipod@songbirdnest.com/components/ComponentLoader.so
b1ef1000-b1ef2000 rw-p 00002000 08:03 16529      /home/frank/.songbird1/0bw1npr4.default/extensions/ipod@songbirdnest.com/components/ComponentLoader.so
b1ef2000-b1ef6000 rw-p b1ef2000 00:00 0 
b1ef6000-b1ef7000 ---p b1ef6000 00:00 0 
b1ef7000-b26f7000 rw-p b1ef7000 00:00 0 
b26f7000-b26f8000 ---p b26f7000 00:00 0 
b26f8000-b2ef8000 rw-p b26f8000 00:00 0 
b2ef8000-b2ef9000 ---p b2ef8000 00:00 0 
b2ef9000-b36f9000 rw-p b2ef9000 00:00 0 
b36f9000-b3739000 r-xp 00000000 08:03 38689      /home/frank/Desktop/Songbird/components/sbProperties.so
b3739000-b373d000 rw-p 0003f000 08:03 38689      /home/frank/Desktop/Songbird/components/sbProperties.so
b373d000-b373e000 ---p b373d000 00:00 0 
b373e000-b3f3e000 rw-p b373e000 00:00 0 
b3f3e000-b3f3f000 ---p b3f3e000 00:00 0 
b3f3f000-b473f000 rw-p b3f3f000 00:00 0 
b473f000-b47d6000 r-xp 00000000 08:03 38680      /home/frank/Desktop/Songbird/components/sbDBEngine.so
b47d6000-b47d9000 rw-p 00096000 08:03 38680      /home/frank/Desktop/Songbird/components/sbDBEngine.so
b47d9000-b47f6000 r-xp 00000000 08:03 38685      /home/frank/Desktop/Songbird/components/sbSQLBuilder.so
b47f6000-b47f8000 rw-p 0001d000 08:03 38685      /home/frank/Desktop/Songbird/components/sbSQLBuilder.so
b47f8000-b48ee000 r-xp 00000000 08:03 38694      /home/frank/Desktop/Songbird/components/sbLocalDatabaseLibrary.so
b48ee000-b48f4000 rw-p 000f5000 08:03 38694      /home/frank/Desktop/Songbird/components/sbLocalDatabaseLibrary.so
b48f4000-b490a000 r-xp 00000000 08:03 38727      /home/frank/Desktop/Songbird/components/sbPlaylistCommands.so
b490a000-b490b000 rw-p 00016000 08:03 38727      /home/frank/Desktop/Songbird/components/sbPlaylistCommands.so
b490b000-b4913000 rw-p b490b000 00:00 0 
b4913000-b4923000 rw-p b4913000 00:00 0 
b4923000-b4924000 r--s 00000000 08:03 904130     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4924000-b4926000 r--s 00000000 08:03 904129     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4926000-b4932000 rw-p b4926000 00:00 0 
b4932000-b495e000 r-xp 00000000 08:03 38691      /home/frank/Desktop/Songbird/components/sbLibraryManager.so
b495e000-b4960000 rw-p 0002b000 08:03 38691      /home/frank/Desktop/Songbird/components/sbLibraryManager.so
b4960000-b49fb000 r-xp 00000000 08:03 361456     /usr/lib/libgstreamer-0.10.so.0.13.0
b49fb000-b49ff000 rw-p 0009b000 08:03 361456     /usr/lib/libgstreamer-0.10.so.0.13.0
b49ff000-b4a00000 ---p b49ff000 00:00 0 
b4a00000-b5225000 rw-p b4a00000 00:00 0 
b5225000-b5300000 ---p b5225000 00:00 0 
b5300000-b5303000 r--s 00000000 08:03 903946     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b5303000-b5307000 rw-p b5303000 00:00 0 
b5307000-b532c000 r-xp 00000000 08:03 361438     /usr/lib/libgstbase-0.10.so.0.13.0
b532c000-b532d000 rw-p 00024000 08:03 361438     /usr/lib/libgstbase-0.10.so.0.13.0
b532d000-b5346000 r-xp 00000000 08:03 361436     /usr/lib/libgstaudio-0.10.so.0.10.0
b5346000-b5347000 rw-p 00018000 08:03 361436     /usr/lib/libgstaudio-0.10.so.0.10.0
b5347000-b534b000 rw-p b5347000 00:00 0 
b534b000-b534c000 r--s 00000000 08:03 904128     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b534c000-b5354000 rw-p b534c000 00:00 0 
b5354000-b5360000 r-xp 00000000 08:03 38703      /home/frank/Desktop/Songbird/components/sbDeviceManager.so
b5360000-b5361000 rw-p 0000b000 08:03 38703      /home/frank/Desktop/Songbird/components/sbDeviceManager.so
b5361000-b536a000 r-xp 00000000 08:03 361448     /usr/lib/libgstinterfaces-0.10.so.0.10.0
b536a000-b536b000 rw-p 00008000 08:03 361448     /usr/lib/libgstinterfaces-0.10.so.0.10.0
b536b000-b536c000 r--s 00000000 08:03 903936     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b536c000-b5378000 rw-p b536c000 00:00 0 
b5378000-b537a000 r--s 00000000 08:03 903935     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b537a000-b537e000 rw-p b537a000 00:00 0 
b537e000-b538e000 r-xp 00000000 08:03 38700      /home/frank/Desktop/Songbird/components/sbGStreamer.so
b538e000-b538f000 rw-p 00010000 08:03 38700      /home/frank/Desktop/Songbird/components/sbGStreamer.so
b538f000-b5393000 rw-p b538f000 00:00 0 
b5393000-b5395000 r--s 00000000 08:03 903929     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b5395000-b539d000 rw-p b5395000 00:00 0 
b539d000-b539e000 r--s 00000000 08:03 903933     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b539e000-b53a6000 rw-p b539e000 00:00 0 
b53a6000-b53cc000 r-xp 00000000 08:03 425179     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b53cc000-b53cd000 rw-p 00025000 08:03 425179     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b53cd000-b53d4000 r-xp 00000000 08:03 425560     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b53d4000-b53d5000 rw-p 00007000 08:03 425560     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b53d5000-b53d6000 ---p b53d5000 00:00 0 
b53d6000-b5bd6000 rw-p b53d6000 00:00 0 
b5bd6000-b5c0c000 r-xp 00000000 08:03 1504509    /lib/libsepol.so.1
b5c0c000-b5c0d000 rw-p 00035000 08:03 1504509    /lib/libsepol.so.1
b5c0d000-b5c17000 rw-p b5c0d000 00:00 0 
b5c17000-b5c66000 r-xp 00000000 08:03 361303     /usr/lib/libgcrypt.so.11.2.3
b5c66000-b5c68000 rw-p 0004e000 08:03 361303     /usr/lib/libgcrypt.so.11.2.3
b5c68000-b5c6b000 r-xp 00000000 08:03 361410     /usr/lib/libgpg-error.so.0.3.0
b5c6b000-b5c6c000 rw-p 00002000 08:03 361410     /usr/lib/libgpg-error.so.0.3.0
b5c6c000-b5c7b000 r-xp 00000000 08:03 361778     /usr/lib/libtasn1.so.3.0.9
b5c7b000-b5c7c000 rw-p 0000e000 08:03 361778     /usr/lib/libtasn1.so.3.0.9
b5c7c000-b5d3f000 r-xp 00000000 08:03 245488     /usr/lib/libasound.so.2.0.0
b5d3f000-b5d44000 rw-p 000c3000 08:03 245488     /usr/lib/libasound.so.2.0.0
b5d44000-b5d46000 r-xp 00000000 08:03 1538078    /lib/tls/i686/cmov/libutil-2.6.1.so
b5d46000-b5d48000 rw-p 00001000 08:03 1538078    /lib/tls/i686/cmov/libutil-2.6.1.so
b5d48000-b5d5c000 r-xp 00000000 08:03 1504508    /lib/libselinux.so.1
b5d5c000-b5d5e000 rw-p 00013000 08:03 1504508    /lib/libselinux.so.1
b5d5e000-b5d6d000 r-xp 00000000 08:03 1538074    /lib/tls/i686/cmov/libresolv-2.6.1.so
b5d6d000-b5d6f000 rw-p 0000f000 08:03 1538074    /lib/tls/i686/cmov/libresolv-2.6.1.so
b5d6f000-b5d71000 rw-p b5d6f000 00:00 0 
b5d71000-b5d7f000 r-xp 00000000 08:03 360046     /usr/lib/libavahi-client.so.3.2.2
b5d7f000-b5d80000 rw-p 0000e000 08:03 360046     /usr/lib/libavahi-client.so.3.2.2
b5d80000-b5d8a000 r-xp 00000000 08:03 360670     /usr/lib/libavahi-common.so.3.4.4
b5d8a000-b5d8b000 rw-p 00009000 08:03 360670     /usr/lib/libavahi-common.so.3.4.4
b5d8b000-b5d8d000 r-xp 00000000 08:03 255005     /usr/lib/libavahi-glib.so.1.0.1
b5d8d000-b5d8e000 rw-p 00001000 08:03 255005     /usr/lib/libavahi-glib.so.1.0.1
b5d8e000-b5df8000 r-xp 00000000 08:03 361406     /usr/lib/libgnutls.so.13.3.0
b5df8000-b5dfe000 rw-p 0006a000 08:03 361406     /usr/lib/libgnutls.so.13.3.0
b5dfe000-b5e32000 r-xp 00000000 08:03 361206     /usr/lib/libdbus-1.so.3.3.0
b5e32000-b5e33000 rw-p 00033000 08:03 361206     /usr/lib/libdbus-1.so.3.3.0
b5e33000-b5e4d000 r-xp 00000000 08:03 361208     /usr/lib/libdbus-glib-1.so.2.1.0
b5e4d000-b5e4e000 rw-p 0001a000 08:03 361208     /usr/lib/libdbus-glib-1.so.2.1.0
b5e4e000-b5e52000 r-xp 00000000 08:03 361050     /usr/lib/libORBitCosNaming-2.so.0.1.0
b5e52000-b5e53000 rw-p 00003000 08:03 361050     /usr/lib/libORBitCosNaming-2.so.0.1.0
b5e53000-b5e73000 r-xp 00000000 08:03 361141     /usr/lib/libaudiofile.so.0.0.2
b5e73000-b5e75000 rw-p 00020000 08:03 361141     /usr/lib/libaudiofile.so.0.0.2
b5e75000-b5e7e000 r-xp 00000000 08:03 255045     /usr/lib/libesd.so.0.2.38
b5e7e000-b5e7f000 rw-p 00009000 08:03 255045     /usr/lib/libesd.so.0.2.38
b5e7f000-b5e86000 r-xp 00000000 08:03 361288     /usr/lib/libgailutil.so.18.0.1
b5e86000-b5e87000 rw-p 00006000 08:03 361288     /usr/lib/libgailutil.so.18.0.1
b5e87000-b5e8e000 r-xp 00000000 08:03 1504498    /lib/libpopt.so.0.0.0
b5e8e000-b5e8f000 rw-p 00006000 08:03 1504498    /lib/libpopt.so.0.0.0
b5e8f000-b5eae000 r-xp 00000000 08:03 361552     /usr/lib/libjpeg.so.62.0.0
b5eae000-b5eaf000 rw-p 0001e000 08:03 361552     /usr/lib/libjpeg.so.62.0.0
b5eaf000-b5ebc000 r-xp 00000000 08:03 361374     /usr/lib/libgnome-keyring.so.0.1.1
b5ebc000-b5ebd000 rw-p 0000d000 08:03 361374     /usr/lib/libgnome-keyring.so.0.1.1
b5ebd000-b5f06000 r-xp 00000000 08:03 361046     /usr/lib/libORBit-2.so.0.1.0
b5f06000-b5f0f000 rw-p 00049000 08:03 361046     /usr/lib/libORBit-2.so.0.1.0
b5f0f000-b5f10000 rw-p b5f0f000 00:00 0 
b5f10000-b5f3f000 r-xp 00000000 08:03 361301     /usr/lib/libgconf-2.so.4.1.2
b5f3f000-b5f42000 rw-p 0002e000 08:03 361301     /usr/lib/libgconf-2.so.4.1.2
b5f42000-b5f98000 r-xp 00000000 08:03 361400     /usr/lib/libgnomevfs-2.so.0.2000.0
b5f98000-b5f9b000 rw-p 00055000 08:03 361400     /usr/lib/libgnomevfs-2.so.0.2000.0
b5f9b000-b5fae000 r-xp 00000000 08:03 361162     /usr/lib/libbonobo-activation.so.4.0.0
b5fae000-b5fb0000 rw-p 00013000 08:03 361162     /usr/lib/libbonobo-activation.so.4.0.0
b5fb0000-b6002000 r-xp 00000000 08:03 361160     /usr/lib/libbonobo-2.so.0.0.0
b6002000-b600c000 rw-p 00051000 08:03 361160     /usr/lib/libbonobo-2.so.0.0.0
b600c000-b6021000 r-xp 00000000 08:03 361129     /usr/lib/libart_lgpl_2.so.2.3.19
b6021000-b6022000 rw-p 00014000 08:03 361129     /usr/lib/libart_lgpl_2.so.2.3.19
b6022000-b6036000 r-xp 00000000 08:03 361370     /usr/lib/libgnome-2.so.0.2000.0
b6036000-b6037000 rw-p 00014000 08:03 361370     /usr/lib/libgnome-2.so.0.2000.0
b6037000-b6066000 r-xp 00000000 08:03 361384     /usr/lib/libgnomecanvas-2.so.0.2000.0
b6066000-b6067000 rw-p 0002f000 08:03 361384     /usr/lib/libgnomecanvas-2.so.0.2000.0
b6067000-b60c2000 r-xp 00000000 08:03 361164     /usr/lib/libbonoboui-2.so.0.0.0
b60c2000-b60c5000 rw-p 0005a000 08:03 361164     /usr/lib/libbonoboui-2.so.0.0.0
b60c5000-b61dd000 r-xp 00000000 08:03 360750     /usr/lib/libxml2.so.2.6.30
b61dd000-b61e2000 rw-p 00118000 08:03 360750     /usr/lib/libxml2.so.2.6.30
b61e2000-b61e3000 rw-p b61e2000 00:00 0 
b61e3000-b626b000 r-xp 00000000 08:03 147183     /usr/lib/libgnomeui-2.so.0.2000.1
b626b000-b626f000 rw-p 00087000 08:03 147183     /usr/lib/libgnomeui-2.so.0.2000.1
b626f000-b6278000 r-xp 00000000 08:03 1538068    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6278000-b627a000 rw-p 00008000 08:03 1538068    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b627a000-b6282000 r-xp 00000000 08:03 1538070    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6282000-b6284000 rw-p 00007000 08:03 1538070    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6284000-b6298000 r-xp 00000000 08:03 1538065    /lib/tls/i686/cmov/libnsl-2.6.1.so
b6298000-b629a000 rw-p 00013000 08:03 1538065    /lib/tls/i686/cmov/libnsl-2.6.1.so
b629a000-b629c000 rw-p b629a000 00:00 0 
b629c000-b62a3000 r-xp 00000000 08:03 1538066    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b62a3000-b62a5000 rw-p 00006000 08:03^A


```
and it just stops there...

---

### Post by justsomedude on 2008-02-09
Songbird 0.4 doesn't need to be installed. Just extract the archive somewhere to your home directory. There will be a file called *Songbird* in the extracted folder, click on it and Songbird starts.

If you want to, you can create a desktop shortcut or a start menu entry for it. That's all.

---

### Post by sub2007 on 2008-02-09
If you prefer, you can get a a .deb version from GetDeb now:

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

