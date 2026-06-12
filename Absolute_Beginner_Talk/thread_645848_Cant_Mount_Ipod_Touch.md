---
title: "Cant Mount Ipod Touch"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by pigeonor on 2007-12-20
I have looked everywhere, and it seems that i am the only one having this problem.  I have been trying to connect my Ipod Touch in Ubunty Hardy Heron using theses: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) instructions.  I am able to get everything to work until i get to the "mount-iphone" command, all i get is the following:

root@pigeon0r-laptop:/home/pigeon0r# iphone-mount
root@192.168.1.3's password: 
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option


can someone/anyone please help me.  i have tried everything that i can think of, and would be very appreciative.

With Regards,

pigeon0r

---

### Post by LowSky on 2007-12-20
your using a very unstable ubuntu release to hook up your ipod

try Gutsy it might work

---

### Post by pigeonor on 2007-12-20
i just tried on my gutsy computer, and i get the exact same message.

---

### Post by superm1 on 2007-12-25
iphone-mount must be run as a user.  **not** root.

Also, make sure your mount point is empty, that the mount point is writable by the fuse group and that your user is in the fuse group.

---

### Post by jazz452 on 2008-01-07
How do you make sure mount point is not empty need a step by step tutorial.I have the same message mount point not empty use nonempty mount option but just dont get any of it.

---

### Post by itsJim on 2008-01-07
I had the same problem. I'm not sure what happened but the ipod wasn't actually mounted at that location, but the files were copied to that location. Make sure your ipod isn't mounted and delete the /media/ipod directory. Then try to mount the ipod again using iphone-mount.

---

### Post by superm1 on 2008-01-11
There is a new version of ipod-convenience that will check to make sure the ipod is accessible before carrying onward.  It will warn you that it couldn't mount, so that this sort of problem doesn't happen.

---

### Post by j_dog on 2008-01-19
> **superm1 said:**
> There is a new version of ipod-convenience that will check to make sure the ipod is accessible before carrying onward.  It will warn you that it couldn't mount, so that this sort of problem doesn't happen.

I am having problems also. For some reason I cant get the ipod convenience installed. it says I need ssh service installed on the device.  I have  open ssh .


I am getting frustrated.

---

### Post by superm1 on 2008-01-20
Is it running?  You can check by running nmap against your device's ip address.

---

### Post by j_dog on 2008-01-21
> **superm1 said:**
> Is it running?  You can check by running nmap against your device's ip address.


This is what it says :

john@john-desktop:~$ nmap 192.168.0.107

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-21 07:49 EST
Interesting ports on 192.168.0.107:
Not shown: 1696 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap finished: 1 IP address (1 host up) scanned in 20.209 seconds
john@john-desktop:~$ 
:-k

I don't know what it means.

I have followed the tutorial on using ipod with Ubuntu.   I must have messed something up !

---

### Post by superm1 on 2008-01-21
> **j_dog said:**
> This is what it says :

john@john-desktop:~$ nmap 192.168.0.107

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-21 07:49 EST
Interesting ports on 192.168.0.107:
Not shown: 1696 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap finished: 1 IP address (1 host up) scanned in 20.209 seconds
john@john-desktop:~$ 
:-k

I don't know what it means.

I have followed the tutorial on using ipod with Ubuntu.   I must have messed something up !
Okay, well try to ssh into it by hand (ssh 192.168.0.107 -l root)

If that works, reconfigure ipod-convenience

```
sudo dpkg-reconfigure ipod-convenience
```

---

### Post by j_dog on 2008-01-21
> **superm1 said:**
> Okay, well try to ssh into it by hand (ssh 192.168.0.107 -l root)

If that works, reconfigure ipod-convenience

```
sudo dpkg-reconfigure ipod-convenience
```


O.K .    I got htis in one terminal :
john@john-desktop:~$ ssh 192.168.0.107 -l root
root@192.168.0.107's password: 
Last login: Mon Jan 21 08:00:28 2008 from 192.168.0.100
# 


Then opened a new terminal  to reconfig. the ipod- convenience.

Whats next ?

when I try to mount, i get:
john@john-desktop:~$ ipod-touch-mounttouch: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.
john@john-desktop:~$ 



Thank you greatly for your help !!!

---

### Post by superm1 on 2008-01-21
> **j_dog said:**
> O.K .    I got htis in one terminal :
john@john-desktop:~$ ssh 192.168.0.107 -l root
root@192.168.0.107's password: 
Last login: Mon Jan 21 08:00:28 2008 from 192.168.0.100
# 


Then opened a new terminal  to reconfig. the ipod- convenience.

Whats next ?

when I try to mount, i get:
john@john-desktop:~$ ipod-touch-mounttouch: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.
john@john-desktop:~$ 



Thank you greatly for your help !!!
Check the permissions on the directory.  It should be owned by root:fuse.

---

### Post by j_dog on 2008-01-21
> **superm1 said:**
> Check the permissions on the directory.  It should be owned by root:fuse.


I'm  sorry,,, How ?



Yes, Root Fuse

---

### Post by superm1 on 2008-01-21
> **j_dog said:**
> I'm  sorry,,, How ?
sudo chown root:fuse /media/ipod

---

### Post by j_dog on 2008-01-21
> **superm1 said:**
> sudo chown root:fuse /media/ipod

john@john-desktop:~$ sudo chown root:fuse /media/ipod
john@john-desktop:~$

---

### Post by kplaxmaster on 2008-01-25
> **itsJim said:**
> I had the same problem. I'm not sure what happened but the ipod wasn't actually mounted at that location, but the files were copied to that location. Make sure your ipod isn't mounted and delete the /media/ipod directory. Then try to mount the ipod again using iphone-mount.

This worked for me.  Simply put:
```
sudo adduser username:fuse
```
This adds us to the fuse usergroup.  If this isn't done so, you must restart the X server, or simply alt+shift+backspace.

Next, make sure /media/ipod is under proper ownership
```
sudo chown -R username:fuse /media/ipod
```

Plugin your ipod... now time to mount it (make sure ipod-convenience is do installed (sudo apt-get ipod-convenience AFTER adding the repository:: deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main -- also make sure you know your iPods IP during the install as it will ask you for it--better to have static one that dynamic!).  

If using ipod touch:
```
ipod-touch-mount
```

if using iphone:
```
iphone-mount
```

[SIZE="4"]If error when mounting[/SIZE]
If no error occured, you are finished! now use amarok or gtkpod or whatever you want to use to synch your ipod-touch/iphone.
note: when mounted, should show up on desktop, thus if it didn't it most likely didn't mount!
If it gives you a weird error about fuse or the mount point isn't empty... then make sure your ipod is umounted (but most likely your ipod wasn't mounted correctly so you dont have to umount anyways... but make sure!)
```
ipod-touch-umount
```
or if iphone:
```
iphone-umount
```

Now remove files from ipod mount location
```
rm -r /media/ipod/
```
If you get an error here, then you prob don't have permission and thus you need to change ownership of the mount point or add yourself to the fuse group (see above).

Now, retry mounting your ipod/iphone with the respective code
```
ipod-touch-mount/iphone-mount
```


----

Now you are all set using your new iphone/ipod!!

Remember, this only works when your iphone/ipod touch has been jailbreaked.  Also note that there is no way to downgrade your iphone firmware version from 1.1.3, however you can downgrade 1.1.3 firmware for the ipod-touch.  In order to do so, you must have access to iTunes (mac or windows).

To downgrade...
[http://www.youtube.com/watch?v=YakjwxB3nQU](http://www.youtube.com/watch?v=YakjwxB3nQU)

Make sure you download the link (press the see more info on the right to get the link to the zip file with the necessary files to downgrade your firmware!).

enjoy

---

### Post by j_dog on 2008-01-25
I am getting closer.....I can feel it ! 

O.K ... kplaxmaster, I am following your instructions.    I thank you greatly !

It no longer shows up as a camera when I plug it in,  but it doesn't show up at all.
I have removed the /media/ipod file.

I 'll bet I just need one more command to be done. 

john@john-desktop:~$ ipod-touch-mount
read: Connection reset by peer
john@john-desktop:~$ rm -r /media/ipod/
rm: cannot remove directory `/media/ipod/': Permission denied
john@john-desktop:~$ sudo rm -r /media/ipod/
john@john-desktop:~$ ipod-touch-mount/iphone-mount
bash: ipod-touch-mount/iphone-mount: No such file or directory
john@john-desktop:~$ ipod-touch-mount/iphone-mount
bash: ipod-touch-mount/iphone-mount: No such file or directory
john@john-desktop:~$ sudo chown -R username:fuse /media/ipod
chown: `username:fuse': invalid user
john@john-desktop:~$ sudo chown -R john:fuse /media/ipod
chown: cannot access `/media/ipod': No such file or directory
john@john-desktop:~$ 

  ?

---

### Post by superm1 on 2008-01-25
Guys:

With the latest version of ipod-convenience, you should **not** have to be rm -rf /media/ipod/*.  If you are having to do this, you have an error with the way things are set up (likely permissions related).

---

### Post by j_dog on 2008-01-25
> **superm1 said:**
> Guys:

With the latest version of ipod-convenience, you should **not** have to be rm -rf /media/ipod/*.  If you are having to do this, you have an error with the way things are set up (likely permissions related).

man, this is getting complicated.
i did see an error about permissions,but I thought it was solved. 

Well anyway,it still dont work.

Thank you all for your kind help.

---

### Post by superm1 on 2008-01-25
Since you added yourself to the fuse group, have you logged out?  What are the current permissions on the ipod directory?

```
ls -l /media/
```

will tell you

---

### Post by j_dog on 2008-01-25
john@john-desktop:~$ ipod-touch-mount
read: Connection reset by peer
john@john-desktop:~$ sudo chown -R john:fuse /media/ipod
john@john-desktop:~$ ipod-touch-mount
iPod is not responding to pings at 192.168.0.107.
Please set the environment variable IGNOREPING if you want to ignore this.
john@john-desktop:~$

---

### Post by superm1 on 2008-01-25
So your ipod isn't responding.  There would be your issue.  Double check the ip address.

If its wrong, then run

```
sudo dpkg-reconfigure ipod-convenience
```

---

### Post by jazz452 on 2008-01-31
Cheers itsjim that helped but forgot to reply:).
Although never got to play the music sent via gtkpod it showed up but would not play.Amarok works fine transfering music and video so will stick with that.Also tried amarok2 with kde4 give it year.  Maybe iphone wont b bricked by then but the way i mess it probably will.

---

### Post by jazz452 on 2008-02-04
Now its serious trouble updated iphone to 1.1.3 and now the music doesnt seem to be stored in the same place.From what i can gather the music is stored at    
   private/var/mobile/Media/iTunes_Control/Music                                                                                  on the iphone.So now nothing works so dont do it till someone has  
sorted it out if any can help it would be greatly appreciated (why did i have to mess :¬) )

---

### Post by CrazyAzazel on 2008-02-04
Yes, I think I now am going reaaaally mad Oo
I am trying for about 3 hours to get my Ipod Touch working on Ubuntu but it wont :'(
I can do what I want, everytime I get the error, that permissions were denied
And also everytime I plug my Ipod in, it shows up as a stupid camera....

and if I add myself to the fuse group it says:
Please add yourself to the fuse group, logout/in and try again.

I badly hope you can help me:/ 
thanks for now,
Azazel

---

### Post by CrazyAzazel on 2008-02-06
sorry for double posting but I really need help >.<
so please?xD

---

### Post by pythonusr on 2008-02-06
> **jazz452 said:**
> Now its serious trouble updated iphone to 1.1.3 and now the music doesnt seem to be stored in the same place.From what i can gather the music is stored at    
   private/var/mobile/Media/iTunes_Control/Music                                                                                  on the iphone.So now nothing works so dont do it till someone has  
sorted it out if any can help it would be greatly appreciated (why did i have to mess :¬) )

Same issue. I updated my iPod touch to 1.1.3, and now I get the "Connection reset by peer" error. I have my IP set as 192.168.1.200 in ipod-convenience and in the touch's wifi settings.

Anyone?

---

### Post by pythonusr on 2008-02-07
Actually, after downgrading back to 1.1.1, I still get the error when trying to mount.

Anyone?

---

### Post by jazz452 on 2008-02-10
Did u try going to ure home directory click on show hidden files scroll down to .ssh folder then delete  
everything in the folder.Then start from the beginning it should create some new keys to ssh in to ure
iphone/ipod.But maybe the update has done something else i have restored to 1.1.1 and havent tried to ssh yet.
Just tried it no problem i used this command in terminal   ( ssh-keygen -t rsa )  Only this time i had to use the password" alpine" which is default it would not work with no password as before.
j@j-desktop:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/j/.ssh/id_rsa): 
/home/j/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/j/.ssh/id_rsa.
Your public key has been saved in /home/j/.ssh/id_rsa.pub.
The key fingerprint is:
48:4c:b8:04:ed:f1:58:14:7f:ac:89:73:ba:83:80:bf j@j-desktop
j@j-desktop:~$ ssh root@192.168.0.3
The authenticity of host '192.168.0.3 (192.168.0.3)' can't be established.
RSA key fingerprint is f8:2e:77:96:68:1f:40:56:89:5a:1f:1f:bf:bf:57:a5.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.3' (RSA) to the list of known hosts.
root@192.168.0.3's password: 
#

---

### Post by jazz452 on 2008-02-10
Updating must have reset everything but i dont think at this time you will be able to transfer anything over till you downgrade to older firmware.As i said earlier nothing is stored in the same place although it will look like everthing is fine believe me it isnt so no options at present but to downgrade to 1.1.1 then update to 1.1.2. Hope this helps someone.

---

### Post by ntetreau on 2008-02-11
I have followed various guides to update my 1.1.2 OTB iphone to 1.1.3 and it works fine with Ubuntu after following the wiki guide.  Make sure you follow it to the letter and if you are on 1.1.3, check that section at the bottom of the wiki:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by jazz452 on 2008-02-13
I see the how to for 1.1.3 but when i updated there were no guides.Still i dont think it is worth upgrading again yet due to various issues.Give it a month and ill give it ago.

---

### Post by xjgnsdof on 2008-02-20
This is so complicated. That's why I use Windows to sync my iPod Touch. Until the community can develop plug-and-play usability, that's what I will continue to use. No headaches. I do, however, use Ubuntu for 98% else.

---

### Post by ntetreau on 2008-02-22
> **elgilicious said:**
> This is so complicated. That's why I use Windows to sync my iPod Touch. Until the community can develop plug-and-play usability, that's what I will continue to use. No headaches. I do, however, use Ubuntu for 98% else.

I hope you will find the degree of support in the next Ubuntu version, Hardy, to be up to your standard.  The iphone and itouch support will come out of the box with gtkpod and Amarok.  The ipod-convenience scripts take care of most of the things underneath.  I doubt that we are at the point where everything is true plug-and-play but solid enough to move away from the plug-and-pray!

---

### Post by pjb42 on 2008-02-22
Hi there,

My friend has just set up my ipod touch in a mac. Now I want a way to mount in in mu ubuntu linux so to transfer my music files. I installed gtkpod, but I donot find my model there. HELP!!

---

### Post by pjb42 on 2008-02-22
Hi there,

My friend has just set up my ipod touch in a mac. Now I want a way to mount in in mu ubuntu linux so to transfer my music files. I installed gtkpod, but I donot find my model there. HELP!!
__________________

---

### Post by ntetreau on 2008-02-23
> **pjb42 said:**
> Hi there,

My friend has just set up my ipod touch in a mac. Now I want a way to mount in in mu ubuntu linux so to transfer my music files. I installed gtkpod, but I donot find my model there. HELP!!
__________________

You seem very excited there, that's good!  Now check out my post up there on the page, follow the link and then follow the guide to the letter.  It looks worst then it is!  After that, you'll be able to sync your music no probs on ubuntu!

---

### Post by psychofish25 on 2008-02-24
Amarok and gtkPod have been annoying me lately, so I am currently working on a project to play music on your iPod, or just access files, via SSH. Since the new 1.1.3, alot of directories have changed and ipod-convenience is slightly buggy. I was wondering if anyone knew what exactly is mounted from the ipod, is it just the music? Also, how can I copy files from my iPod to my Desktop via SSH?

---

### Post by jazz452 on 2008-02-26
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
Is the place to go it works very well indeed as stated earlier in this post.I use amarok to transfer music and video wirelessly.Hope this helps.

---

### Post by agentnixon on 2008-06-01
> **kplaxmaster said:**
> This worked for me.  Simply put:
```
sudo adduser username:fuse
```
This adds us to the fuse usergroup.  If this isn't done so, you must restart the X server, or simply alt+shift+backspace.

Next, make sure /media/ipod is under proper ownership
```
sudo chown -R username:fuse /media/ipod
```

Plugin your ipod... now time to mount it (make sure ipod-convenience is do installed (sudo apt-get ipod-convenience AFTER adding the repository:: deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main -- also make sure you know your iPods IP during the install as it will ask you for it--better to have static one that dynamic!).  

If using ipod touch:
```
ipod-touch-mount
```

if using iphone:
```
iphone-mount
```

[SIZE="4"]If error when mounting[/SIZE]
If no error occured, you are finished! now use amarok or gtkpod or whatever you want to use to synch your ipod-touch/iphone.
note: when mounted, should show up on desktop, thus if it didn't it most likely didn't mount!
If it gives you a weird error about fuse or the mount point isn't empty... then make sure your ipod is umounted (but most likely your ipod wasn't mounted correctly so you dont have to umount anyways... but make sure!)
```
ipod-touch-umount
```
or if iphone:
```
iphone-umount
```

Now remove files from ipod mount location
```
rm -r /media/ipod/
```
If you get an error here, then you prob don't have permission and thus you need to change ownership of the mount point or add yourself to the fuse group (see above).

Now, retry mounting your ipod/iphone with the respective code
```
ipod-touch-mount/iphone-mount
```


----

Now you are all set using your new iphone/ipod!!

Remember, this only works when your iphone/ipod touch has been jailbreaked.  Also note that there is no way to downgrade your iphone firmware version from 1.1.3, however you can downgrade 1.1.3 firmware for the ipod-touch.  In order to do so, you must have access to iTunes (mac or windows).

To downgrade...
[http://www.youtube.com/watch?v=YakjwxB3nQU](http://www.youtube.com/watch?v=YakjwxB3nQU)

Make sure you download the link (press the see more info on the right to get the link to the zip file with the necessary files to downgrade your firmware!).

enjoy

thanks! this worked perfectly!

---

### Post by matheuu on 2008-07-16
hello all. I have spent more than a few hours more like days.. trying to get some songs off my ubuntu laptop onto a bloody itouch thing... Can some one explain. If I have tried one of these methods and it didnt work...will my system be stuffed.. Do I have to remove or reset anything? are there files in my laptop that are stopping me from trying the tutorials again? I cant get it to work! Could anyone walk me thought the set up... with really easy explanations at to what I could possibly be doing wrong?

HELP!! Please???

---

