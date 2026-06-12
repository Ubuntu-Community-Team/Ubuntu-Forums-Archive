---
title: "Graphics drivers? and internet connection"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-02-07
Well I have Ubuntu up and running and the partitions worked perfectly!

But i have a few little issues one is I'm not sure how to set up my internet (I have wireless belkin router).

The other issue is there is an obvious problem with graphics because there are about 6 lines down the screen that appear to be as far as i can see "distorting the graphics" but i presume i have to have internet on Ubuntu before i can tackle that.


Thanks,

Travis

---

### Post by wormser on 2008-02-07
It would help us if we new more about the hardware.  Post the results of the following command.

```
lspci
```

---

### Post by travismoore on 2008-02-07
Will do might take a minute because of booting.

---

### Post by jan quark on 2008-02-07
well perhaps one of these guides will fit your belkin card

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

please post the result of 

```
lspci
```

and check on this site if your card works with the ndiswrapper application
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by travismoore on 2008-02-07
Here is result:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Unknown device 0183 (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

```

My belkin wireless adapter is USB if that helps.

USB Adapter (belkin) says its F5D7050

Router is: F5D7633-4


That first guide looks right. Now i have to use my USB flash hdd to do everything its really annoying lol.

---

### Post by travismoore on 2008-02-07
Bump =D

---

### Post by travismoore on 2008-02-07
I'm stuck on the guide([https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")) because there is a newer version of the driver (with a different file name and format and im not sure how to change the commands to compensate for that.

File is called:
2008_0117_RT73_Linux_STA_Drv1.1.0.0.tar.bz2

and its located on my desktop in a folder called FIX


```
You can get the driver into your current directory with the following wget command:

user@ubuntu:~$ wget http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz 

Step 4 - Extract and prepare the archive

Using tar extract the archived driver and change directory into the build area. Note, this is the "Module" sub-directory of the extracted tree.

user@ubuntu:~$ tar xvzf RT73_Linux_STA_Drv1.0.3.6.tar.gz  
user@ubuntu:~$ cd RT73_Linux_STA_Drv1.0.3.6/Module
user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ 

```

Thanks,

Travis

---

### Post by travismoore on 2008-02-08
Bump

---

### Post by kesman on 2008-02-08
try this
```

cd FIX

```
to go to the folder with the driver.
Then type
```

tar xvzf

```
and press TAB-key to see all the possibilities. If there's only the driver you need, then type in few of the first letters of it and press TAB again to complete the name for you. After this, it extracts the contents of the file to a folder that you can see with command ls. Go to that folder, remember to use TAB again for completion of folder or file names, it makes things so much easier.

---

### Post by travismoore on 2008-02-08
cheers will give that ago.

---

### Post by travismoore on 2008-02-08
When I typed: 
```
cd FIX
```
In the command terminal i get this error:

No such file of directory (or something similar).

---

### Post by kesman on 2008-02-08
you said you had a directory called FIX in your home? Apparently, there isn't. Linux is case-sensitive, so FIX is different from fix. Check with ls the contents of your home-folder.
[B]
SORRY! I didn't notice that the folder was on your desktop. Go to desktop with cd Desktop in your home, and then proceed to the FIX-folder.
[/B]

---

### Post by travismoore on 2008-02-08
cool cheers

---

### Post by travismoore on 2008-02-08
Ok I navigated to the file using:
```
cd Desktop/FIX
```
and that worked.


then I did:
```
tar xvzf
```

and i got this code back:
```
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.

```

---

### Post by travismoore on 2008-02-08
Bump

---

### Post by kesman on 2008-02-08
You didn't read carefully. Tar xvzf AND THEN PRESS TAB to see a list of files to be opened with tar.

---

### Post by travismoore on 2008-02-08
> **kesman said:**
> You didn't read carefully. Tar xvzf AND THEN PRESS TAB to see a list of files to be opened with tar.

oh ok sorry :mad:

---

### Post by justsomedude on 2008-02-08
It's 

```
tar **-**xvzf *name of archive*
```

Or, you could just right click and select "extract here"...

---

### Post by travismoore on 2008-02-08
Oh i see.

---

### Post by travismoore on 2008-02-08
```
travis@Travis:~$ cd Desktop/FIX
travis@Travis:~/Desktop/FIX$ tar -xvzf 2008_0117_RT73_Linux_STA_Drv1.1.0.0.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
```

help?

---

### Post by kesman on 2008-02-08
so you see the file on your desktop. Maybe try right-click on it and "extract here" or something.

---

### Post by travismoore on 2008-02-08
Oh right i have done that already into the another folder.

I just dont really understand what some of these terminal commands do so I'm finding ti hard to follow.

---

### Post by kesman on 2008-02-08
now that you have extracted the files from the tar.gz2 package, follow the manual normally, and remembter to use TAB to autocomplete the filenames ni the terminal commands.

---

### Post by travismoore on 2008-02-08
> **kesman said:**
> now that you have extracted the files from the tar.gz2 package, follow the manual normally, and remembter to use TAB to autocomplete the filenames ni the terminal commands.

k, cheers =D

---

### Post by travismoore on 2008-02-08
```
travis@Travis:~$ fromdos *
The program 'fromdos' is currently not installed.  You can install it by typing:
sudo apt-get install tofrodos
bash: fromdos: command not found
travis@Travis:~$ 
travis@Travis:~$ sudo apt-get install tofrodos
[sudo] password for travis:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tofrodos

```

Yet more problems dosn't seem to have this "from dos" thing..

---

### Post by justsomedude on 2008-02-08
Check your spelling... ;)

---

### Post by travismoore on 2008-02-08
oh right didn't see that just copied straight from the guide lol

---

### Post by justsomedude on 2008-02-08
Hm... Just checked the guide you're using,

```
sudo apt-get install tofrodos 
```

should work, actually. :confused:

---

### Post by travismoore on 2008-02-08
Yea thats what i realized tried fromdos as well but wasn't sure.

I'm not having much joy with Ubuntu yet also have graphics issues lol, but once i have the internet working it should be easier to sort out.

---

### Post by justsomedude on 2008-02-08
Well, it's not an easy beginning for you, I assume that doing all this can be quite overwhelming in the beginning. 

You graphics problem won't be as hard, but wireless can be a bi**h to set up.

Please run

```
sudo apt-get update
```

and post the output here.

---

### Post by travismoore on 2008-02-08
OK, brb gonig to boot into linux and thne boot back into windows after to post results lol.

Its not really do bad because i have done some light programming in the past just annoying really =D

---

### Post by justsomedude on 2008-02-08
> **travismoore said:**
> OK, brb gonig to boot into linux and thne boot back into windows after to post results lol.


Aha! Here we go, you are not connected to the internet.

I assume you're using this guide:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

This guide assumes you are connected to the web. The command *apt-get* downloads and installs software, this is why it doesn't work.

Can you connect via cable?

---

### Post by travismoore on 2008-02-08
what type of cable? (my xbox has an ethernet one would that work?) i also probably have some other internet cables around (dono what they are though).

```
travis@Travis:~$ sudo apt-get update
[sudo] password for travis:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done

```

On an unrelated note what are the shortcuts for copy and paste?


And yea that is the guide im using.

---

### Post by justsomedude on 2008-02-08
Standard ethernet cable should do, the xbox one sounds fine. Otherwise, try what you've got lying around, until you can connect under Ubuntu.

There are ways to do this offline, but it will make things a lot easier.

> On an unrelated note what are the shortcuts for copy and paste?

Mark the text and then middle click. :)

---

### Post by travismoore on 2008-02-08
OK cheers hoepfully il post from Ubuntu soon.

---

### Post by travismoore on 2008-02-08
Ok im on the net bow through ethernet. So I'll try the set up now.

---

### Post by travismoore on 2008-02-08
```
travis@Travis:~$ sudo apt-get install tofrodos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tofrodos

```

I'm getting the same problem even though im on the internet now.

---

### Post by justsomedude on 2008-02-08
Do 

```
sudo apt-get update
```

first, then:

```
sudo apt-get install tofrodos
```

If you still get the same error go to System --> Administration --> Software Sources and make sure your software sources are enabled.

---

### Post by travismoore on 2008-02-08
Cheers worked perfectly.

---

### Post by travismoore on 2008-02-08
```
travis@Travis:~$ Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$ cp Makefile.6 Makefile

```

I get an error back saying:

```
bash: Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$: No such file or directory

```

any ideas?

---

### Post by justsomedude on 2008-02-08
Well, in the directory you're at, is there a file called Makefile.6 ?

---

### Post by travismoore on 2008-02-08
Yep in the module directory there is a makefile.6 and a makefile (along with 20 or so other files).

---

### Post by justsomedude on 2008-02-08
Lol, just downloaded the driver to check. The instructions work, make sure there are no typos. Remember, these commands are case sensitive...

---

### Post by travismoore on 2008-02-08
I can't work out what i am doing wrong, the guide says this:
```
user@ubuntu:~/RT73_Linux_STA_Drv1.0.3.6/Module$ cp Makefile.6 Makefile
```

My file is located at:

Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module

and the Module folder contians the Makefile.6 and Makefile

but I don't know if i am getting the command right i put in this:

```
travis@Travis:~$ Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$ cp Makefile.6 Makefile
```

Cheers,

Travis

---

### Post by justsomedude on 2008-02-08
^^looks okay... (Edit: No it does not)

Make sure there is no space between "$" and "cp". Could you post the exact error message?

Or, simply delete Makefile and then rename Makefile.6 to Makefile.


Edit:

You have to change to the directory first:

```
cd ~/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module
```

Then

```
cp Makefile.6 Makefile
```

---

### Post by travismoore on 2008-02-08
> **justsomedude said:**
> 
Or, simply delete Makefile and then rename Makefile.6 to Makefile.

That would make more sense.

---

### Post by travismoore on 2008-02-08
```
travis@Travis:~$ Module$ gedit rtmp_def.h
bash: Module$: command not found
travis@Travis:~$ Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$ gedit rtmp_def.h
bash: Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$: No such file or directory

```

Is it worth moving them to a different directory if it will work better?

---

### Post by justsomedude on 2008-02-08
^^No.

What you don't understand is how to navigate inside the terminal. Look, when you open it, it probably says:

```
travis@Travis:~$
```

This means you are in your home directory.

You have downloaded and extracted your files to /home/Travis/Desktop//Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0. Inside this folder, there is another folder called "Module".

This is where we do all our work, so we have to navigate there first. The command

```
cd
```

means **c**hange **d**irectory. We have to specify where we want to go so we add ~/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module.


So do:
```

cd ~/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module
```

and then 

```
gedit rtmp_def.h
```


You can do it! :)

---

### Post by travismoore on 2008-02-08
Ahh i get it now =D

cheers that worked!

---

### Post by travismoore on 2008-02-08
```
travis@Travis:~/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$ make clean
rm -rf *.o *~ .*.cmd *.ko *.mod.c .tmp_versions built-in.o
travis@Travis:~/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
In file included from /home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rt_config.h:198,
                 from /home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:31:
/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_def.h:852: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token
/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_def.h:852: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_def.h:852: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_def.h:852: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_def.h:852: error: expected identifier or &#8216;(&#8217; before &#8216;}&#8217; token
/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:65: error: expected expression before &#8216;;&#8217; token
make[2]: *** [/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/travis/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
travis@Travis:~/Desktop/Help/2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module$ 

```

Got this error when using the make clean and make commands (i think thats creating the driver or installing im not sure)

---

### Post by travismoore on 2008-02-08
Bump

---

### Post by justsomedude on 2008-02-08
Post your rtmp_def.h and the output of 

```
lsusb
```

---

### Post by travismoore on 2008-02-08
> **justsomedude said:**
> Post your rtmp_def.h and the output of 

```
lsusb
```

heres the rtmp_def.h:
[http://www.megaupload.com/?d=QN5DL9ZG](http://www.megaupload.com/?d=QN5DL9ZG)


Result of lsusb:
```
travis@Travis:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 004 Device 001: ID 0000:0000  

```

---

### Post by justsomedude on 2008-02-08
The file is temporarily not available on Megaupload.

Anyway, you can attach text files here. ;)

---

### Post by travismoore on 2008-02-08
It says the text file it to big to upload will find some where to put in in a second.

[http://www.2shared.com/file/2819628/282c5c5b/rtmp_def.html](http://www.2shared.com/file/2819628/282c5c5b/rtmp_def.html)

---

### Post by justsomedude on 2008-02-08
Scroll down to the bottom of the file. There is an empty line (line 852). This is what he complains about. 

You will have to add

```
{USB_DEVICE(0x050d,0x7050)}, /* Belkin F5D7050 ver 1000 */      \
```

To that file. You can use the empty line. Maybe the above is wrong and it is 

```
{USB_DEVICE(0x050d,0x7050)}, /* Belkin F5D7050 ver 1000 WiFi */      \
```


Keep in mind you have to take care about the syntax and you have to get everything right...

---

### Post by travismoore on 2008-02-08
Ok cheers I'll try that.

That worked with the (make and make clean) will proceed with install now.

---

### Post by kesman on 2008-02-08
Hey maybe you just keep using the wired network and work out the wireless stuff later?

---

### Post by travismoore on 2008-02-08
I'm on step 6 now but I'm not sure where to get the details about my router.

link to guide:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by justsomedude on 2008-02-08
The first thing I would do now is reboot and see if your driver is listed in the restricted drivers manager.

Then, see if maybe the Network Manager Applet works with it (though I doubt it), the guide is a little old and linux progresses fast...

Congrats, you have now compiled something and become a geek. Goodbye sunshine, you will never find a girlfriend again. :D


For the information:

MY_ESSID = Name of your Network
wireless-key s = Your wireless password

Both are things you have to know, even when you configure your wireless on Windows...

---

### Post by travismoore on 2008-02-08
> **justsomedude said:**
> 
Congrats, you have now compiled something and become a geek. Goodbye sunshine, you will never find a girlfriend again. :D
 HA HA :lolflag:

Well I restarted and it pop up at the top i click on the belkin router and it appears to be working 100%. 

Should i start a new thread to deal with my graphics problems?

Thanks a million for being so patient =D,

Travis

---

### Post by justsomedude on 2008-02-08
^^No Problem.

I think a new thread would be fine, it's just me here left anyway and I know nothing about your video card.

Have fun... :)

---

### Post by travismoore on 2008-02-08
Well its stopped working again now ...

I say connected and it fails.

Any Ideas?

---

### Post by travismoore on 2008-02-08
Heres a screenshot if that helps.

---

### Post by travismoore on 2008-02-09
10 hour bump

Guide i used:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

