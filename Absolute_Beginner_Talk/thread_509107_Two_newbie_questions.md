---
title: "Two newbie questions"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by John Macnab on 2007-07-25
Hi :)
I'm new to all this so please be gentle:) I am currently downloading the updates for my Ubuntu which number around 100 and is taking a pretty long time.Is there some way I can store these updates in a CD once I have downloaded them?
Also, I installed Firestarter and it is not showing up in my menu list.What could I do about that?Thank you for your patience.

---

### Post by AceofSpades19 on 2007-07-25
firestarter is in system > administration
or you can type the command "firestarter" without the quotes in the terminal

---

### Post by amac777 on 2007-07-25
I believe all the downloaded packages will be saved in /var/cache/apt.

---

### Post by John Macnab on 2007-07-25
Thank you for the kind replies, both of you :)*feeling quite silly coz I never thought of looking into the system menu to see whether firestarter was there*
Can I just copy /var/cache/apt folder into a cd and later use it to update when I reinstall Ubuntu?
Again, thanks very much for the replies- and so quick too :)

---

### Post by sad_iq on 2007-07-25
The simplest way to do what you want...and more: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by amac777 on 2007-07-25
> **John Macnab said:**
> Thank you for the kind replies, both of you :)*feeling quite silly coz I never thought of looking into the system menu to see whether firestarter was there*
Can I just copy /var/cache/apt folder into a cd and later use it to update when I reinstall Ubuntu?
Again, thanks very much for the replies- and so quick too :)

I know there is information available about making a local apt repository. 
For example you can get more help here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Personal_Apt_Repository](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Personal_Apt_Repository)

According to that information, I might have also been wrong about where the debs are stored. It looks like they are in /var/cache/apt/archives...

If all you are trying to do is prevent having to redownload them all from a clean install, you might be able to just copy the *.debs from your CD backup to /var/cache/apt/archives on your newly installed system and then re-update that system. Those debs would not need to be redownloaded but any newer ones would be and all should work.

Let me know if it works! :) I'm interested in the result but I'm not in front of my ubuntu box to try it right now.

---

### Post by hyper_ch on 2007-07-25
well, you can copy the .deb files form /var/apt/cache and at a later time (after reinstall or simliar) you just copy them back there (just make sure the permissions are ok).

---

### Post by John Macnab on 2007-07-25
Ty Sad-iq, I'll try aptoncd.
Amac, I'll try copying the archive files and see how that goes too and I'll get back :) Erm,how do I re-update from the cd? Just copy the files to the archive folder?*Sorry I am absolutely hopeless with puters*
Ty,Hyper_ch- I didnt see your post first time sorry- I dunno how that happened

---

### Post by amac777 on 2007-07-25
> **John Macnab said:**
> Ty Sad-iq, I'll try aptoncd.
Amac, I'll try copying the archive files and see how that goes too and I'll get back :) Erm,how do I re-update from the cd? Just copy the files to the archive folder?*Sorry I am absolutely hopeless with puters*
Ty,Hyper_ch- I didnt see your post first time sorry- I dunno how that happened

Copying the folders back into the folder might be enough to prevent redownload. Otherwise you might have to setup a CD repository and the other links people above have provided would help do that.

---

### Post by John Macnab on 2007-07-25
Right , sir.Although, I am a really inexperienced noob and I am trying to avoid command lines right now until I know a wee bit more about Linux hehe.
Hmm I just tried copying the files back to the archives for apt but I cant paste files in there.No permission I suppose?And I dont have a clue as to how to go about rectifying that.

---

### Post by hyper_ch on 2007-07-26
there's no reason to avoid the command line... it is a wonderful thing that's why superior to anything Windoze can do ;)

If you don't know what a command can do, have a look at the man pages.

e.g.
```

sudo cp /path/to/org /path/to/dest

```
that command has two commands:
- sudo
- cp

Sudo is used to run the following command as root (administrator). To find out more about "sudo" just enter this in the terminal:
```

man sudo

```
That will open the manual pages for that command. You can navigate through them with the arrow keys and page-up/down keys. To exit the man pages just hit the "q" (quit) key.

So there's the other command, the "cp" one which is short for "copy". Have a read on how to use it and what the paramters do with:
```

man cp

```

with that you can easily find your way around.

---

### Post by John Macnab on 2007-07-26
Well sir, I had burned the apt back up files on a CD in a folder named "aptbackup". I copied it to my desktop and tried the cp command as you said,but I just couldnt get it right.Just kept saying something like :couldnt stat aptbackup ,there aint no such directory! Btw,sir, ty for that quick lesson on cp and on how to use the help pages.Hopefully I'll be able to use command line soon too(I hope!):)One question though if I may- what do I do to copy all files in a directory?Use *.*?
RIght now I'll try the aptoncd to see whether that works.Ty for your help:)
(One bad news is that with everyone helping me out so kindly I'll always be back with all sortsa nutty questions :p)

---

### Post by ugm6hr on 2007-07-26
> **John Macnab said:**
> Right , sir.Although, I am a really inexperienced noob and I am trying to avoid command lines right now until I know a wee bit more about Linux hehe.
Hmm I just tried copying the files back to the archives for apt but I cant paste files in there.No permission I suppose?And I dont have a clue as to how to go about rectifying that.

You can do this with GUI - but you need to start the File Manager (nautilus) with *sudo* rights to write to /var/cache.  So, try this:
```
gksudo nautilus
```

This will allow you to copy the .deb files back.

---

### Post by John Macnab on 2007-07-26
Whee thank you sir. I did that and I am updating the system :) tyvm. 
Amac,sir, it did work , just by copying the contents of the archive.
I still need to learn the commands dont I.Btw I was working in  my root account but it still wouldnt lemme paste into the archive.Is that normal? Or did I do something wrong while creating accounts or something?*Very happy to have avoided downloading all those files again* And these updates ought to work in Kubuntu too right?
Ty everyone :)

---

### Post by amac777 on 2007-07-26
> **John Macnab said:**
> Right , sir.Although, I am a really inexperienced noob and I am trying to avoid command lines right now until I know a wee bit more about Linux hehe.
Hmm I just tried copying the files back to the archives for apt but I cant paste files in there.No permission I suppose?And I dont have a clue as to how to go about rectifying that.

well, at least rectifying getting permissions is easy. If you want to use nautilus (the file manager) to copy the files, just type this at the command line:
```
sudo nautilus
```
You will need to enter your password and then that will open the file manager with root permissions and you will be able to paste anything anywhere. Hope that helps.

EDIT: I see someone already told you how to open nautllus with root permissions above so ignore this post. Glad to hear it worked.

---

### Post by hyper_ch on 2007-07-26
copying all files from a directory to another one would be:

```

cp /path/to/dir/* /path/to/destination/

```

If you don't have the right you may need to use sudo or other variations like:

```

sudo cp -pf ...

```

---

### Post by doomster on 2007-07-26
i dont recall firestarter to be installed on a clean installation of Feistyfawn. if i am true, to install it type
```
 sudo apt-get install firestarter
``` 
this will put it also under the menu System>Administration :)
and welcome to ubuntu! :D

---

### Post by John Macnab on 2007-07-26
Amac, sir, ty for your reply :)
Hyper_ch, thank you for that bit about copying. :)
Doomster, thank you for the welcome sir :D. I have installed firestarter and am now trying to get it to autostart with my Ubuntu.Tried the firestarter's options, also tried setting 'sudo firestarter' in session settings but havent got it right yet.I suppose after I make a change in the command I'll have to restart the machine and not just log out?

---

### Post by hyper_ch on 2007-07-26
Firestarter is just a simple frontend for iptables... no need to have it started upon boot ;)

---

### Post by lemonseed on 2007-07-26
Just think of Firestarter as an options menu to your firewall. The firewall is always there but you'll have to load the menu to make changes to it.

---

### Post by John Macnab on 2007-07-26
Thank you for your replies, sirs :) So even if I dont start firestarter the firewall is already there blocking nasty incoming traffic?Goodies!I searched a little bit and for some people 'sudo firestarter' seems to work, for others, not. Does that ummm mean Ubuntu is umm capricious?

---

### Post by ugm6hr on 2007-07-27
> **John Macnab said:**
> Whee thank you sir. I did that and I am updating the system :) tyvm. 
Amac,sir, it did work , just by copying the contents of the archive.
I still need to learn the commands dont I.Btw I was working in  my root account but it still wouldnt lemme paste into the archive.Is that normal? Or did I do something wrong while creating accounts or something?*Very happy to have avoided downloading all those files again* And these updates ought to work in Kubuntu too right?
Ty everyone :)

Learning Terminal commands (at least basic ones) is useful.  But if you want to be able to access all of your hard drive (to write to / paste files) without using Terminal - it is easy to set up a panel or menu "shortcut" with the command *gksudo nautilus* for future use.  I use XFCE rather than GNOME, but I can't imagine it's hard.  So that you can see what I mean, I've attached a screenshot of the mouse pointer (that you can't see) over my panel shortcut, with the "Properties" box open for the command (my XFCE command is gksudo thunar).

I suspect you weren't working in your root account at all.  This is because Ubuntu specifically makes it difficult to log in as root.  This is for your own safety.  This explains the difference: [http://www.psychocats.net/ubuntu/security#sudoisnotroot](http://www.psychocats.net/ubuntu/security#sudoisnotroot)

The updates should work on Kubuntu7.04, although I think the *gksudo* command is *kdesu* in Kubuntu (perhaps a Kubuntu user could confirm?)

---

### Post by doomster on 2007-07-27
to make firestarter load at startup,you need to set it not to ask for root password.
to do so just : 
```
  gksudo gedit /etc/sudoers 
```

add this line to the end of file

```
username ALL= NOPASSWD: /usr/bin/firestarter
```

dont forget to replace the username with your login name.:)

to make firestarter minimize on start , in session  startup programs add it with this command
```
 sudo firestarter --start-hidden
```

P.S: making firestarter not to ask for password may risk your security a bit

have fun

---

### Post by John Macnab on 2007-07-27
Thank you for explaining the root and admin stuff,Ugm6hr.And all this while,sir, I was thinking my admin account was the root.*sheepish grin*:)

Well, Doomster, sir, I am too scared to risk the security stuff so I guess I'll not try to start firestarter up at the beginning anymore. I'm writing down the commands anyway though hehe.tyvm for the reply:)
I just created a new user account and in that I cant bring up firestarter at all coz it keeps asking me for the password I use for administrative tasks and it doesnt accept the password for my admin account that I use for synaptic and in console in my admin account.(Sorry I had asked the same question among others in a newer post please dont get peeved off)

---

### Post by doomster on 2007-07-27
try using the password of your newlly created account, and see if it works

---

### Post by ugm6hr on 2007-07-27
> **John Macnab said:**
> I just created a new user account and in that I cant bring up firestarter at all coz it keeps asking me for the password I use for administrative tasks and it doesnt accept the password for my admin account that I use for synaptic and in console in my admin account.(Sorry I had asked the same question among others in a newer post please dont get peeved off)

Simple test:
try *gksudo nautilus* in Terminal from the new user account

If it doesn't work - then the new user account has been set up as a "Desktop user" rather than "Administrator".  If you want the new user to have access to "sudo" commands, then you have to change the settings in "Users and Groups" to allow them to "administer the system".  

Unfortunately, because I'm on Xubuntu, the settings pages might look slightly different on my system, so you'll have to look around the System Menu for something that looks like this.

---

### Post by John Macnab on 2007-07-27
Doomster, sir,the password of the account I am in doesnt work either :(
Ugm6hr,sir,I did set the account up as desktop user*sheesh*.I thought a non admin user would be allowed access to the firestarter atleast.A desktop user is supposed to move around only on the puter itself, and not the net?*scratching head*

---

### Post by ugm6hr on 2007-07-27
> **John Macnab said:**
> Ugm6hr,sir,I did set the account up as desktop user*sheesh*.I thought a non admin user would be allowed access to the firestarter atleast.A desktop user is supposed to move around only on the puter itself, and not the net?*scratching head*
Errrmmm.... :confused:

Why do you need Firestarter to get on the net?  If it is for internet security, then I think you have misunderstood what Firewall does.

Firestarter is not strictly a firewall; it is more correctly a GUI to modify the true firewall *iptables.*.  The firewall (iptables) is always running, whether you have Firestarter running or not.

The reason a desktop user cannot access Firestarter is because it allows you to reduce your computer's security (by opening firewall ports etc), so only Administrators can do this.

If you have some strange network that requires firewall port manipulation each time you want to get online (I am not a networking expert), then all users will have to have Admin rights.

---

### Post by John Macnab on 2007-07-27
Oops!So thats why desktop users dont get to run firestarter. ABout running sudo sir, I wasnt using the command line interface while trying to bring up firestarter in my desktop account.I just clicked on firestarter option in the systems menu and it asked me to type the admin passy in the window that popped up and it wouldnt accept it.And as I understand from your words, thats ok coz desktop users arent allowed to use admin passy- is that right sir?

---

### Post by Mornedhel on 2007-07-27
Desktop users can administer as long as they know the password of one of the sudoers (or root's, if his account is enabled). In both cases, they effectively are administrators. You probably typed something wrong.

---

### Post by ugm6hr on 2007-07-27
> **John Macnab said:**
> Oops!So thats why desktop users dont get to run firestarter. ABout running sudo sir, I wasnt using the command line interface while trying to bring up firestarter in my desktop account.I just clicked on firestarter option in the systems menu and it asked me to type the admin passy in the window that popped up and it wouldnt accept it.And as I understand from your words, thats ok coz desktop users arent allowed to use admin passy- is that right sir?

Firestarter automatically adds a run command to the menu with *gksudo*, which is why you are asked for the password when running from the menu.  This is because Firestarter does not run without sudo rights.

Although... Mornedhel says this is not the issue. I'm not 100% certain - I only have 1 user on my Ubuntu system.  Perhaps worth trying to run Firestarter from your main Admin login user to check whether it works there (it will still ask for password - same as your Admin login).

---

### Post by Mornedhel on 2007-07-27
> **John Macnab said:**
> it asked me to type the admin passy in the window that popped up and it wouldnt accept it.And as I understand from your words, thats ok coz desktop users arent allowed to use admin passy- is that right sir?

I was only correcting him on this particular point, because it's fairly obvious that if desktop users cannot use a sudoer's password, then who will (assuming that a "desktop user" is "every user except root in person") ?

---

### Post by ugm6hr on 2007-07-27
> **Mornedhel said:**
> I was only correcting him on this particular point, because it's fairly obvious that if desktop users cannot use a sudoer's password, then who will (assuming that a "desktop user" is "every user except root in person") ?
I think there are root, Administrator, Desktop User, Unprivileged users.

Not 100% certain, but I think they work something like:
Administrator: do anything with sudo
Desktop: Free access to all devices (e.g. CD drive, scanners etc)
Unprivileged: Can't access devices

Only Admin accounts have access to sudo control (as Admin suggests).

---

### Post by Mornedhel on 2007-07-27
Actually, only users listed in the /etc/sudoers will be able to sudo root (the behaviour of sudo when you don't specify another user to impersonate). The group 'admin' is in there.

Rephrasing everything I previously said :

"Desktop users" can sudo as root, unless configured otherwise.

(There, much clearer, isn't it ?)

---

### Post by ugm6hr on 2007-07-27
> **Mornedhel said:**
> Actually, only users listed in the /etc/sudoers will be able to sudo root (the behaviour of sudo when you don't specify another user to impersonate). The group 'admin' is in there.

Rephrasing everything I previously said :

"Desktop users" can sudo as root, unless configured otherwise.

(There, much clearer, isn't it ?)

Cheers for clearing that up.  That's why I love helping out here - I learn new stuff all the time :)

---

### Post by John Macnab on 2007-07-27
Hi :)
Ugm6hr,sir,I can run firestarter from my admin account, it doesnt have any problems with the password there.
Mornedhel,sir, I tried my admin passy many times, taking care to type it in slowly so's not to make any mistakes but it still says incorrect password(as I said, I am typing the passy in the pop up window not console).I am pretty sure it isnt a spelling mistake, sir

---

### Post by ugm6hr on 2007-07-27
> **John Macnab said:**
> Hi :)
Ugm6hr,sir,I can run firestarter from my admin account, it doesnt have any problems with the password there.
Mornedhel,sir, I tried my admin passy many times, taking care to type it in slowly so's not to make any mistakes but it still says incorrect password(as I said, I am typing the passy in the pop up window not console).I am pretty sure it isnt a spelling mistake, sir

As discussed, the likelihood is that your new user has been configured not to have sudo (Firestarter) access.  After what I said about the Firewall - does this matter?

If so - go back to Users / Groups and look for something like the screenshots attached, and tick the box *Administer the System*, or create a new user as *Administrator*.

---

### Post by John Macnab on 2007-07-27
Oh sorry sir, actually the firestarter does not matter, in the light of what you said. I was just worried about how to get my password to be recognized as the correct one.If I allow administrator rights, then my user account's password itself will be ok for admin password wouldnt it? I was merely thinking of how to make it so that the admin password of my original administrator account would be recognized as the password to authorize administrative tasks.(Gawd I have a positive genius to write in a confusing way dont I- sorry)

---

### Post by ugm6hr on 2007-07-27
> **John Macnab said:**
> Oh sorry sir, actually the firestarter does not matter, in the light of what you said. I was just worried about how to get my password to be recognized as the correct one.If I allow administrator rights, then my user account's password itself will be ok for admin password wouldnt it? I was merely thinking of how to make it so that the admin password of my original administrator account would be recognized as the password to authorize administrative tasks.(Gawd I have a positive genius to write in a confusing way dont I- sorry)

I think only the "root" password works with sudo - and that is the same as your initial Administrator user.  But I'm not 100% certain on this.

---

### Post by John Macnab on 2007-07-27
Um, sir, I allowed the desktop user account to have rights to administer the system and it accepts the password I set up for the desktop user.

---

### Post by ugm6hr on 2007-07-28
> **John Macnab said:**
> Um, sir, I allowed the desktop user account to have rights to administer the system and it accepts the password I set up for the desktop user.

I stand corrected :)  Glad it is all sorted now.

---

### Post by John Macnab on 2007-07-28
Well sir, *coughing embarrasedly* I think I am a bit toooo dense, because um, if I have to give admin rights , well, why does the desktop user account ask for a passy when it doesnt have any admin rights?Why have firestarter listed in there at all if desktop user cant run it anyway? Wouldnt it have been better to make it so that the administrator could enable stuff for the desktop user without giving dekstop user administrative rights?I mean I might want to let someone else use the puter and run firestarter too but what if I dont want to give him admin rights?I would rather have gone and enabled firestarter for him using my administrator passy, thus ensuring that only I have admin rights

---

### Post by ugm6hr on 2007-07-28
I'm afraid you're asking questions I don't know the answer to now!  

But I suspect the reason is that there is no way to allow an administrator function to run using a non-administrator account, because once it is running, the non-administrator would have access to it (and could potentially potentially harm your computer).  

As for why it appears in the menu - I'm sure that GNOME/Ubuntu has a menu editor - so perhaps you could edit that yourself for desktop users, to remove all System entries that require administrator passwords.  

I don't know that any operating system automatically removes menu functions for non-admin users...

Perhaps someone else might comment.

---

### Post by Mornedhel on 2007-07-28
> **John Macnab said:**
> Why have firestarter listed in there at all if desktop user cant run it anyway?

Because someone has bo be able to run it, right ? The Ubuntu paradigm is :

the first user created is also a member of the admin group by default;
the admin group is able to administer via sudo by default;
the root account is disabled by default;

Thus in the standard desktop situation, you only have one user that also is administrator, but usually doesn't have his rights enabled.

> **John Macnab said:**
> Wouldnt it have been better to make it so that the administrator could enable stuff for the desktop user without giving dekstop user administrative rights?I
He can, in theory. He could make a firestarter group, able to use firestarter without administrative rights, and then make the desktop user a member of the firestarter group.

I think you need some background on the Linux permissions system, and as I have some free time right now, let's go.

I have already explained the sudo mechanism a few posts earlier, be sure to check out the sudo man page as well. (Man pages are great. Can't stress this enough. We need a laaaarge warning sign to display whenever someone posts a new thread here, in big red letters : "Have you RTFM ?")

Now for what used to be the permissions system before the popularisation of sudo : basically, there's root, and there's Joe Sixpack. root is as close to God as you get as far as this particular machine is concerned : root does not care about permissions, root always has rwx on every single file. (r stands for read permission, w for write permission, x for execute permission ; in the case of folders, r is ls, w is touch/rm, x is cd.)

Joe Sixpack on the other hand is a standard, desktop user. Now there are many many possibilities for Joe to be able to perform an action "a" (a being r, w or x) on a file. Any given file has three sets of permissions : owner, group, others. The owner is most of the time the user who has created the file. The group is by default the group consisting of only the owner. The others are any users not belonging to the group and not impersonating the owner. (Ownership and group can be changed with chown and chgrp, permissions with chmod.) Thus Joe can only do "a" on the file if :

1. he impersonates the owner and the owner has the "a" permission or if
2. he belongs to the group and the group has the "a" permission or if
3. the "others" have the "a" permission (think world-readable files).

sudo allows you to impersonate a user, by default the root user, if you know his/her password and are listed in the sudoers file. I am myself more used to su, which basically spawns a new shell impersonating any user (but take into account the fact that I *do* sometimes use the real root account, which is a bit dangerous).

Now in this case, Joe can run firestarter if he belongs to a group (let's call it the firestarter group) which has the "x" permission set to true for the firestarter program. (The default for firestarter is to be affiliated to the root group, and that should *not* be changed unless you are very very sure it will not compromise anything (it probably will).)

Now for my very last question : Why on earth do you want a non-administrator to change the rules of your firewall ?

Edition : Argh, this took me so long to post ugm6hr managed to answer before I did. ugm6hr, your suspicions are truthy (not an actual word). GNOME's menu editor is Alacarte and was moved from Applications/Accessories to System/Preferences, "Main Menu". GNOME *does* automatically remove administration entries by the way, once you create an user that does not belong to "admin".

---

### Post by John Macnab on 2007-07-28
Hello :)
Thank you for the replies , both of you :)
Ugm6hr, sir,I'll do what you said, I'll just remove that Firestarter entry from the menu.(Gawd I am one big pest arent I! I am really slow on the uptake, sorry)

Mornedhel, sir, thank you very much for taking the pain and trouble to write that lengthy lesson for me.(Um I do try the man pages here and there but it looks so scary to me! *).I've understood a bit of what you said but as I said, I absolutely suck at logic- especially puter/programming logic is entirely beyond me- unlike you people who are born for this kinda thing!*sniff*And taking your advice, I am leaving Firestarter alone. You are going to laugh at this but I actually use Firestarter to look at the hits I get on my machine and see where it could be coming from.No, not backtracing or anything but I know my IP and I assume most of the other IP addresses alloted by my ISP must have a similar number allotment?I frankly get my own IP from the firestarter's list, I dunno how to get it otherwise.But yes, I dont want someone else to change my firewall settings so, yes, I am leaving it all alone.Again, ty for the lesson-Please dont feel you wasted your time, you didnt!

---

### Post by ugm6hr on 2007-07-29
> **John Macnab said:**
> I frankly get my own IP from the firestarter's list, I dunno how to get it otherwise.
Depending on what GUI you use to connect to the internet, that might give you your IP (e.g. Wicd has it displayed if you roll your mouse pointer over the Wicd icon in system tray.

Otherwise, from Terminal:
```
ifconfig
```

---

### Post by John Macnab on 2007-07-29
Thank you very much for that, sir. Didnt know you could use different GUI's to connect.However that dun matter does it?:)

---

### Post by ugm6hr on 2007-07-29
> **John Macnab said:**
> Thank you very much for that, sir. Didnt know you could use different GUI's to connect.However that dun matter does it?:)

Not if your network connection works!

---

### Post by amac777 on 2007-07-29
To find out your computer's external IP address just go here:

[http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/)

---

### Post by John Macnab on 2007-07-29
Ugm6hr,sir, well I asked for that one didnt I :p
Amac, sir, ty for that address- that does have tools for finding out locations of other ips too.whee!tyvm

---

