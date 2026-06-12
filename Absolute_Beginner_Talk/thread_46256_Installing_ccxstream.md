---
title: "Installing ccxstream"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by s1k3st on 2005-07-03
First of all I have to say: Ubuntu has to be the best linux distro out there!  I've tried so many different ones, but always found myself going back to windows.  Well, anyway over the last few days I have completely switched to linux.  I've found that most all the software installation is simple (thx to apt), but I wish I could figure out how to install ccxstream.  Since this is the first program I've had to compile I'm kinda lost.  I got the "make" command to work, but when I try to "make install" I get the error "No rule to make target `install'.  Stop.".  If someone could please give me a hand I would be forever grateful.

---

### Post by poofyhairguy on 2005-07-04
Umm...

> ccxstream is a streaming media server for xbox media center.

I hate installing from source. If I was you, I would take this rpm:

[http://ninja.no/apt/9/i386/RPMS.local/](http://ninja.no/apt/9/i386/RPMS.local/)

and make it into a deb.

[http://www.ubuntuforums.org/showthread.php?t=38526&highlight=zsnes](http://www.ubuntuforums.org/showthread.php?t=38526&highlight=zsnes)

that howto of mine will tell you how.

I can't help you otherwise.

---

### Post by s1k3st on 2005-07-04
Thanks for the help, I think I got it installed, but I'm not sure on how to run it.  I know, I'm really showing my linux newb-ness, but it would be nice if someone could tell me how I go about getting it up and running.

EDIT: Nevermind, I didn't get it installed, lol.  But seriously can someone please help me.  I'm so lost!

---

### Post by ignatz42 on 2006-03-07
I know this is an old thread but it was the only hit I got when I searched Google for ccxstream unbuntu  so I thought it might be useful.

I was able to build ccXStream from source by:

1. Download the latest version of the code for Linux:
[http://osdn.dl.sourceforge.net/xbmc/ccxstream-1.0.15.tar.gz](http://osdn.dl.sourceforge.net/xbmc/ccxstream-1.0.15.tar.gz)

2. Untar the files:
tar xvf ccxstream-1.0.15.tar.gz

3. Change directories
cd ccxstream-1.0.15

4. Attempt to build the files
make

Output:
...
cc -lreadline -ltermcap  ccxstream.o ccxfile.o ccutil.o ccbuffer.o ccdebug.o ccx mltrans.o ccxencode.o   -o ccxstream
/usr/bin/ld: cannot find -lreadline
collect2: ld returned 1 exit status
make: *** [ccxstream] Error 1

5. Search Google for various parts of the error message till I figured out that -lreadline was caused by lack of GNU readline libraries.

6. Install missing libraries:
I searched Synaptics Package Manager for readline and found that I had libreadline4 and libreadline5 selected so I added libreadline5-dev and clicked Apply.

-or-

sudo apt-get install libreadline5-dev

7. Attempt to build the files again.
This time I got a couple of build warings but no errors.  Now, just use the README file to launch the ccXStream server.

You may also wany to try Samba to share files as well.

---

### Post by LaLLi on 2006-03-09
Thank You ignatz42.

I had this problem a few months ago, but I solved it just like you. Exept I wasnt smart enough to document what I did and I certainly didn't post the resolution to ubuntuforums.org for future generations. :)

---

### Post by ExZen on 2006-11-02
I'm having a problem following this guide, I'm pretty new to this.  When I enter "tar xvf ccxstream-1.0.15.tar.gz" in the command line I get this:

tar: ccxstream-1.0.15.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

the file is located on my desktop...am I missing something?

---

### Post by LaLLi on 2006-11-03
Are you writing that tar command in the sama place your tar file is at? If it is on your Desktop open your terminal and write:
1. cd Desktop
2. ls ccxstream*
If the file is here it shold be listed now. If it is you can continue with the tar command int the original guide. Allways use Tab to compelete you pakage names incase the name of the pakage has changed.

---

### Post by ExZen on 2006-11-03
Thanks, that worked great!  For lack of an OS, I've had to switch to using Ubuntu full time and its been a rocky transition at points.

that said, I don't suppose you have a few tips as to how to use ccxstream after this process is complete?  I have the folder with the files in it, but I have no idea what comes next, and I havn't had much luck finding a useful guide.

Thanks for your help

---

### Post by LaLLi on 2006-11-03
I Use Ubuntu 99.9% of the time and sometimes boot into some MS OS I happend to have installed. I changed ccXstream for samba because its much easier to use and its allready installed in Ubuntu. I have all my data shared to my Xbox and I watch a lot of videos over from my samba share.

I had some problems with samba but most of them were related to using FAT32 for my data. Now all my data is on Ext3 and it works.

---

### Post by ExZen on 2006-11-03
Really?  How did you get Samba to work?  I installed it in Ubuntu, and set my folders to share, but I cannot access anything through XBMC.

---

### Post by LaLLi on 2006-11-04
First of all I configured Firestarter to allow Samba connections for my Xbox. My Xbox has a static IP. Add the Xbox IP to the "Allow connections from host" list in the policy page. Next allow service Samba(ports 137-139, 445) for the Xbox IP.

Do you have a recent version of XBMC? XBMC had a major version release recently and one change was the way you connect to shares. No more need to edit XML file.

I don't remember was it necessary for me to edit /etc/samba/smb.conf manually. What I have noticed that Samba shares will not work if the forlder you are sharing has some complex folder/file names. Im not sure wether its because they are too long or have stange characters. Workgroup shoud be same for both the PC nad the Xbox.

Here is a portion from my smb.conf for comparison.
[global]
workgroup = WORKGROUP
security = SHARE
server string = Ubuntu
wins support = no

[hdb1]
path = /media/hdb1
read only = Yes
guest ok = Yes
available = yes
browseable = yes
public = yes
writable = no

---

### Post by ExZen on 2006-11-04
Is firestarter insalled by default in Ubuntu?  I can't find any info about a firewall...I used a text command earlier to flush my firewall settings, so even if there was one previously, there shouldn't be one anymore.

My version of xbox media center is a new one, I installed it in september.

I set my music and movies folders to share through SMB, but I still cannot access them through XBMC...

How do I "allow service Samba(ports 137-139, 445) for the Xbox IP"?  

Sorry for the complete newbness, just having a hard time figuring out how some things work.

---

### Post by LaLLi on 2006-11-04
Install Firestarter. It is a easy way to configure IP-tables with a GUI. It is in the repos.

sudo apt-get install firestarter

Once installed it can be found at
System > Administration > Firestarter

In Firestarter there are 3 tabs.
1. Open the policy tab.
2. Right click "Allow connections from host" area and select "Add rule".
3. Write the Xbox IP here and as for comment use "Xbox"(not necessary).
4. Right click "Allow service" area and select "Add rule".
5. Click the "Name" selection and select "Samba(SMB)" from the list.
6. Select "When source is" as IP and enter your Xbox IP.(so your Samba cant be accessed by no one else)

---

### Post by ExZen on 2006-11-04
I did as you said, but still no luck.  when I try to access videos through XBMC I get "cannot detect network" or some such thing.  Could it have to do with my connection?  My computer is attached to my xbox via a router, which worked fine under windows.

---

### Post by LaLLi on 2006-11-05
What is your XBMC IP-address? What is your Ubuntu IP-address? If your router works with Windows it works with any OS. Do you have a NAT on your Internet connection?

..I shoud propably write a How-To on this topic..

---

### Post by ExZen on 2006-11-08
that would wonderful lol.  I've still had no luck getting this working.

Ubuntu IP:  *NEWB ALERT* As I just discovered, I have no idea to find my IP in Ubuntu.

Xbox IP: According to the evox dashboard its 192.168.1.108.  However, I do not have the static IP turned on, and I'm getting the feeling that it should be.

Also, there are two IP's in my dashboard, both just labelled "IP"

On is in blue, and is the one I provided above.  The other is in white and is located under static IP, and it 192.168.0.2

---

### Post by ExZen on 2006-11-08
under network settings --->  DNS the IP reads 192.168.2.1.  My wired connection is set to DHCP rather than static IP in Ubuntu.

---

### Post by dannyboy79 on 2006-11-08
if you have a router between your lan and the internet I wouldn't suggest messing with iptables or installed firestarter but that's up to you. i also have a samba setup and share tons of movies, music, and pics to 2 xbox's running xbmc 2.0.

---

### Post by ExZen on 2006-11-08
I have another problem...I marked 2 folders as a NFS share, and whenever I try to delete them now, they delete, but when I refresh the share window they're their again...for some reason azeureus is now sharing my desktop lol.  And no matter what I try, they always reappear!

---

### Post by dannyboy79 on 2006-11-08
i can tell ya 1thing, when i was using winbloz previously and couldn't get my shares to show up in xbmc, i installed ccxstream, added the folders to ccxstream I wanted to be available, restarted the ccxstream server, and then within xbmc, all you do is go to xbmp (auto discover) i think that's what it is, your shares should show up, that was the easiest way ever. but then when I moved to ubuntu, I didn't know ccxstream was available so i spent the time to setup samba (i am glad i did this because I have 4 computers on my lan and 2 xboxs). So I would suggest if you want to have a temporary solution so you can watch some of your avi files, continue with what you doing as far as installing and setting up ccxstream and you should be golden! i wish i could help you with ccxstream in linux but I only know how to use it in winbloz but it can't be that different, just make sure you add your shares to the ccxstream config or whatever, then make sure it's server is running possibly by running [code=]ps aux[/code] that'll show you all the current processes on your linux box whether they are running or not. there has to be a guide for ccxstream in linux since I am sure that's where it started and then was probably ported to winbloz. that's the case for a lot of software. LONG LIVE OPEN SOURCE!!!

---

### Post by ExZen on 2006-11-13
Ugh, still no luck getting my shares up and running...this is really frustrating...is there a link to a guide or something anyone knows of?  I'm on a dozen different threads being told a dozen different methods, none of which seem to work.

It'd be really nice having a guide on how to do this properly...

---

### Post by gree on 2006-11-28
try editing the file /etc/sysconfig/xbmspd
there you have the options:

# ROOTDIR=-
# USER=nobody
# LISTEN=0.0.0.0
# PORT=1400
# PASSWORD=
# SYMLINKS=no
# BROADCAST=yes
## MOUNTS="video=/foo/video/. music=/foo/mp3/."  
## COMMENT=hostname

testing this right now. will edit the comment with the results.

--1st try: nada...

---

### Post by moonlightcheese on 2008-02-03
i can get ccxstream to run.  compiled with the libreadline5-dev package installed.

```
./ccxstream -r /media/disk
```
/media/disk is a 850GB raid5 with 774 permissions...

but XBMC won't see it... dunno what gives...

---

### Post by LaLLi on 2008-02-04
Why would you install ccxstream? XBMC and Ubuntu work well together using Samba. Thou I have one small problem. XBMC doesnt want to access some folders. It open one folder without problems then asks for authorization on another folder...and no nothing works for username.

---

### Post by moonlightcheese on 2008-02-04
> **LaLLi said:**
> Why would you install ccxstream? XBMC and Ubuntu work well together using Samba. Thou I have one small problem. XBMC doesnt want to access some folders. It open one folder without problems then asks for authorization on another folder...and no nothing works for username.

because samba only works sometimes...  i'm starting to really dislike ubuntu...

---

### Post by LaLLi on 2008-02-04
OK so you have ccxstream running but XBMC cant see it? Is the network connection between PC and Xbox functional? Do you have a firewall on Ubuntu that stops ccxstream packages?

---

### Post by moonlightcheese on 2008-02-04
> **LaLLi said:**
> OK so you have ccxstream running but XBMC cant see it? Is the network connection between PC and Xbox functional? Do you have a firewall on Ubuntu that stops ccxstream packages?
unless this firewall is installed by default, then no.  i had samba working great for all of 2 hours and then after a reboot that quit working.  i can't even get proftpd to work properly...

---

### Post by LaLLi on 2008-02-05
Weird. I have just installed Ubuntu after hardware upgrade. I didn't do any special setups to install Samba. I just went to System -> Administration -> Shared Folders. It asked what protocols to install. I selected Samba since i dont use NFS. The I changed workgroup name from general properties tab and added a share with default properties to shared folders tab. After that I went to XBMC and changed my SMB workgroup name to match Ubuntu and added a shared folder from Video category.

---

### Post by moonlightcheese on 2008-02-05
i couldn't get samba to work out of the box.  i followed a guide and used smbpasswd to enable the samba users after i completed the setup.  i really don't know what to do at this point.  i got it working randomly at some point, along with proftp, but after a reboot it unfixed itself somehow and i have no idea what happened.

however, on a side note, i'm really unimpressed with Ubuntu.  as far as i'm concerned, all software, including samba and proftpd, should operate much more simply.  i want everything that runs that application to be changed in a configuration file somewhere... not some wacky data store where UUID's fall from the sky.  i think i need to switch distros...  this is too much like Windows for me.

---

