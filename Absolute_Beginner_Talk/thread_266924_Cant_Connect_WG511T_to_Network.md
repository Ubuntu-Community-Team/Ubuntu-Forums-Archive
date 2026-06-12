---
title: "Cant Connect WG511T to Network"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by bobaj on 2006-09-27
In windows my WG511T card will not connect to my home network.  I've disabled the security settings for my wireless router and I still can not connect.  My ath0 connection lists "idle" and my signal strength is 0%.  I reloaded my driver using ndiswrapper and the driver from the original winxp disk.  Any help would be appreaciates

Thanks
Bobj

---

### Post by x64Jimbo on 2006-09-28
You should't be using ndiswrapper for Atheros chipset cards. There is a native linux driver for those cards called madwifi. Check it out.

---

### Post by bobaj on 2006-09-28
Hi:

thanks for pointing me in the right direction.  I am a beginner who has just installed Ubuntu.  I've downloaded madwifi and am going through the installation process, however I'm having some problems getting the scripts to execute.  I'm hoping you can help.

When i run the ommand ifconfig wifi0 down - I get
wifi0: ERROR while getting interface flags: No such device

I went on through the scripts running
./madwifi-unload.bash
./find-madwifi-modules.sh /lib/modules

nothing happens.  The instructions say wifi0: ERROR while getting interface flags: No such device
that I should be asked if I want to remove old files, but it doesn't.

I go on to cd .. and run the command
make

I get the following error
/bin/sh: line 0: cd: /lib/modules/2.6.15-27-386/build: No such file or directoryMakefile.inc:89: *** /lib/modules/2.6.15-27-386/build is missing, please set KERNELPATH.  Stop.

any suggestions?

Thanks
Bobaj

---

### Post by x64Jimbo on 2006-09-28
Atheros cards show up as "ath0" instead of wifi0, wlan0, eth1, etc. Try that first.

---

### Post by bobaj on 2006-09-28
I had the card showing up on ath0 and now it doesn't show up.  The card did show up under ifconfig and iwconfig - now ath0 doesnt show up under either.  I ran dmesg and at the bottom it shows a bunch of ath lines which show that drives are unloaded or no routers present.

With the error above I tried to run 
sudo apt-get install build-essential
which did create a bunch of files
I then tried 
sudo apt-get install build-essential linux-headers 'uname -r" which indicates that the newest version is present
These suggestions were found in another thread.

Now ath0 doesn't work at all.  Any suggestions?

---

### Post by x64Jimbo on 2006-09-29
sudo modprobe madwifi
sudo ifconfig ath0 up

---

### Post by bobaj on 2006-09-29
I really appreaciate your help, but the commands don't work.  I believe it is because I can not compile the code into a driver.  I ran the commands and got (transcribing here since I'm on another computer)

FATAL: Module madwifi not found

for the ifconfig command I can get ath0 to show in the Network Settings pannel as active, but cannot get ath0 to show in connection properties.

The problem I am having with compiling madwifi is an error I get when running sudo make

/bin/sh: line 0: cd: lib/modules/2.6.15-27-386/build: no such file or directory Makefile.inc:89: *** /lib/modules/2.6.15-27-386/build is missing, please set KERNELPATH. Stop.

I've run apt-get build-essential.  I've checked ./lib/modules  and there is a folder for 2.6.15-27-386.  But there is no folder called build.

I downloaded madwifi-0.9.2.tar.gz and extracted it in my home directory.  Inside the directory scripts I ran 
./madwifi-unload.bsh
./find-madwifi-modules.sh /lib/modules
In the directory madwifi-0.9.2 I ran
sudo ./make
which failed.

Any help is very appreaceated.
Bobj

---

### Post by x64Jimbo on 2006-09-29
Try this:
[http://www.ubuntuforums.org/showthread.php?t=75451](http://www.ubuntuforums.org/showthread.php?t=75451)

---

### Post by bobaj on 2006-09-30
Hi:

I hate to keep bothering you, but [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz) is no longer available.  The page [http://madwifi.otaku42.de](http://madwifi.otaku42.de) is indicated as archived.  There is a link  which takes me to a download site, however, none of the files starts with madwifi-cvs.  There are some files in an madwifi-old directory, but I am hesitant to try one, in case it is something different which will screw up my installation.  Do you know an alternate site, or alternate file?

Thanks
Bobj

---

### Post by x64Jimbo on 2006-09-30
[http://madwifi.org/](http://madwifi.org/)
First hit from Google search for "madwifi"

---

### Post by bobaj on 2006-10-01
Hi:

I'm feeling really bad.  I already searched the entire madwifi.org site and could not find the cvs version.  When I ran the wget command I got an 404 error message, so I went and manually looked at the http: link in the wget command and did get a 404 error.  I then searched the entire madwifi site and could only find archives neither of which were for -cvs.

On your recommendation, I searched it again and could not find anything. There is a note that points to a .rpm file, but I don't know what to do with that file. 

I must be missing something I just can not find a madwifi-cvs-current.tar.gz.  I'm waiting to see if there is something in Alioth which indicates they have "deb" packages.  I assume that deb is for debian and debian is underlying the Ubuntu system.

I don't know what to say, other than I don't see what I'm suposed to see.

My apologies
Bobj

---

### Post by x64Jimbo on 2006-10-02
Why do you need the cvs version? cvs is usually the really bleeding edge and you shouldn't use it unless you absolutely need a new feature that's not in stable yet.

---

### Post by bobaj on 2006-10-02
Hi

I'm sorry.  I've only been at this for a week.

I don't know what the abbreviations cvs and ng, mean.  I am following the instructins explicityly and the file they indicate to retrieve is a cvs file.  That is why I looked for the cvs file.  I queried the articles and I got some threads that said use ng and some that said don't use ng.  None of the threads said to use current, which does make the most sense.  I didn't go for current because I thought cvs was an acronym for some special compilation which needed to be used by Ubuntu or something.

I appreaciate your help, it has been considerable.  I found someone to come by and he got my wifi running.  I am on madwifi.  The problem continued until we modified the ifconfig file.  It seemed that the DCHP parameters were not getting into the correct file through the GUI interface.  Manually typing them probably solved the problem.  The last step was to set the router to automatic for WEP, the card connected and came to life.  

Again, thanks for all of your help.

Cheers,
bobj

---

### Post by x64Jimbo on 2006-10-02
Glad you got it working and that you have someone to mentor you in Linux. Sure beats learning everything the hard way.

---

