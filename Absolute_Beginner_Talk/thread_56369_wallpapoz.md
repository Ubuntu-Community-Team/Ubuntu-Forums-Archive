---
title: "wallpapoz"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-12
Hi,

My system crashed and i'm having to reinstall everything. 

Wallpapoz - [http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)

downloaded the application and the two dependencies libglademm-2.4 and libxml++2.10 I installed dependencies using Synaptic and it is clear that they are installed.

Then in shell i untarred the wallpapoz app in /tmp 
cd'd wallpapoz
make but it keeps coming up that libxml++ is not there!

I've gone ahead anyways and sudo checkinstalle'd but wallpapoz doesn' t come up, so i've uninstalled as suggested sudo dpkg -r blahablah

Does anyone have any idea why libxml++2.10 is not being read when it is clearly installed. I can only presume that is the reason why wallpapoz is not working after installation.

Any voices of reason welcome,

--
sophtpaw


Addendum:

I just checked again. what i'm getting in terminal is that libxml++2.6 is in fact missing. Which is strange because at the wallpapoz website it is recommending ++2.10 which i presume is a more recent version. 
Regardless i've checked and both ++2.6 and++2.10 are installed according Synaptic

Help...

--
sophtpaw

---

### Post by Tomy on 2005-09-24
**I posted this in an old thread yesterday and have reposted it here. I have marked the other post so hopefully someone will respond here. ** > Originally Posted by **merinda**
  [i]New version of wallpapoz is out. It supports multiple wallpapers per workspace.
[http://wallpapoz.sf.net]("http://wallpapoz.sf.net/")

Dependencies is rather complex. Install them in order:
libxml++-2.10
libsigc++-2.0
glibmm-2.4
gtkmm-2.4
libglademm-2.4
... Regards,
Akbar  [/i]
                                Here is what I did but it does not work. I am running Ubuntu Hoary 5.04.
 
I entered all commands from a root login. I suppose you could put sudo in front of all the commands.

 Downloaded two files:
# wget -c [http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2]("http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2")
 # wget -c [http://members.iinet.net.au/~gracey88/libxml++-2.10.0-1_i386.deb]("http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb")
 
Then I installed libxml++-2.10 from  manicka's deb.
 # dpkg -i libxml++-2.10.0-1_i386.deb
 
 I then installed the dependencies: (note: these are not the exact libs from Akbar's instructions)
 # apt-get install libsigc++-2.0-dev
 # apt-get install libglibmm-2.4-dev
 # apt-get install libgtkmm-2.4-dev
 # apt-get install libglademm-2.4-dev
 
 and then 
 # tar -jxvf wallpapoz-0.2.tar.bz2
 # cd wallpapoz-0.2
 # make
 # sh install.sh /usr
 
 Everything seemed to work okay. But when I click on Applications>Accessories>Wallpapoz nothing happens.
 
 When I run it from the command line I get this error message:
 ~ $ wallpapoz
 wallpapoz: error while loading shared libraries: libxml++-2.6.so.2: cannot open shared object file: No such file or directory
 
 I may have had the original version of wallpapoz on this machine at one point. I think libxml++-2.6.so.2 was needed for that.
 
 Any suggestions. I am running hoary.
 
 Thanks
 Tomy

---

### Post by Ramses on 2005-09-24
if you have libxml++-2.10.so.2 in your /usr/lib directory. You could link it to libxml++-2.6.so.2. I don't really know if this works but you could try it.
 
```
sudo ln -s /usr/lib/libxml++-2.10.so.2 /usr/lib/libxml++-2.6.so.2
```

---

### Post by Tomy on 2005-09-27
[quote=Ramses]if you have libxml++-2.10.so.2 in your /usr/lib directory. You could link it to libxml++-2.6.so.2. I don't really know if this works but you could try it.
 
```
sudo ln -s /usr/lib/libxml++-2.10.so.2 /usr/lib/libxml++-2.6.so.2
```[/quote] Thanks, but I didn't need to try that. I installed a library with a similar name (the "-" is not in front of the 2):

$ sudo apt-get install libxml++2.6

and now it works.

Tomy

Update:
I wrote a HOWTO: Install "wallpapoz"
You can find it here:
[http://www.ubuntuforums.org/showthread.php?t=69507]("http://www.ubuntuforums.org/showthread.php?t=69507")

---

