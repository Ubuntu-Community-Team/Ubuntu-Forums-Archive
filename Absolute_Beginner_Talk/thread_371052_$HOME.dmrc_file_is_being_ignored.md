---
title: "$HOME/.dmrc file is being ignored"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by hoarsecourser on 2007-02-26
What did I do!?  More importantly, what can I do to fix it?  When I log in I get the following message:

"User's $HOME/.dmrc file is being ignored.  This prevents the default sessin and language from being saved.  File should be owne dby user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."

Thanks,

Utter beginner

---

### Post by taurus on 2007-02-26
Did you install something that screwed up the permissions of your $HOME or did you change it?  Boot into recovery mode from GRUB menu and at the prompt, do, assuming your log in name is **john**.

```
chmod 644 /home/**john**/.dmrc
```
Reboot and see if you can log in again.

```
shutdown -r now
```

---

### Post by MkfIbK7a on 2007-02-26
this is usually due to the fact that either that file or your home directory no longer belongs to you and is in the hands of root

AND that is ussually due to graphical sudo

see here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

yes i forgot in the message it says it must have 644 permissions

/me slaps himself on the head

EDIT: woah taurus that was fast!

---

### Post by hoarsecourser on 2007-02-26
I seem to have gone and made it worse now.  When I put in my username and password, now I get a dialogue box that says:

Your home director is listed as: '/home/wiglaf' but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session.

I click yes and it goes to the message I posted earlier.  But instead of logging in like it did before...when I click "Ok" I get:

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try loggin in with one of the failsafe sessions to see of you can fix this problem.

The details "(~/.xsession-errors file)" reads:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/ubmp -x "/var/lib/gdm/:0.Xservers" -h "" - ":0" "username"
/etc/gdm/Xsession: eginningsession setup...

(gnome-session:4923): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission Denied
Could not create per-user gnome confuiguration directory '/home/username/.gnome2/': Permission Denied

---

### Post by hoarsecourser on 2007-02-26
I forgot to add that this is the same for all users.  And I forgot to check spelling.

---

### Post by hoarsecourser on 2007-02-26
Well, Edgy's getting re-installed now.  Luckliy I have data backups.

---

### Post by ricardisimo on 2007-03-22
I used ```
gksudo nautilus
```to change permissions on my home folder (so other users can't access it). Now I'm getting the above error. Mind you, it worked; the permissions are how i want them. But I'm assuming that there is another, correct, and much less GUI-oriented way of setting permissions. What's to be done here? Thanks.

---

### Post by ricardisimo on 2007-03-23
OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

---

### Post by Wiebelhaus on 2007-04-02
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.


thanks bud.

---

### Post by dpcamp on 2007-05-22
I'm getting the same error, but .dmrc is not in my home directory.. whats wrong?

---

### Post by taurus on 2007-05-22
What's the output of this command from a terminal?

```
ls -la ~
```

---

### Post by dumbjaw on 2007-05-24
nice job richardismo.

---

### Post by ricardisimo on 2007-06-09
I still have a few questions about this:
[LIST=1]
[*]Why does non-root Nautilus have options for changing permissions if they won't work?
[*]Why does root-Nautilus have options for changing permissions if they don't work properly?
[*]Is this a Gnome issue (my guess) or linux-image issue?
[*]Is this one of those annoying little blips, like the fake error message one gets when going sudo in Nautilus, that is simply not on anyone's radar for getting fixed ever?
[/LIST]
Just curious. Thanks again.

---

### Post by gcy on 2007-06-10
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

I Had the same problem:
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

I followed your suggestion and fixed my problem.
I don't know how I got the problem, the last thing I did was trying to get AVG to work.
Thanks....:D

---

### Post by nbayiha on 2007-06-12
Thanks   ricardisimo  , I got this problem yesterday but i was tired first try in the morning with your  advice and i got it worked. 
Thanks you.

---

### Post by stewacide on 2007-06-12
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

1000000 thank-yous. 700 did the trick.

---

### Post by Brian96 on 2007-06-21
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

Can anybody help me? :(

I was having the .dmrc being ignored error, so I used these instructions to fix it (except I used 644 permissions instead of 700). Then I got past the login screen without error, but I started getting the "your session lasted less than 10 seconds" error. The output file said it could not create the /home/.gnome2 directory.

Well, I got in this mess--I think--because when I first started in Ubuntu a couple of months ago I wanted to share data between XP and Feisty, so I created a couple of folders. But before I learned to change permissions on folders, I had moved these folders into the /home directory. When that didn't do everything I wanted I started changing permissions. Everything worked fine--except the .dmrc error after login.

Because when I manually changed permissions for my home folder I had ticked the option for applying the changes to all files in the directory, I re-ran the second two commands above with -hR. This also made no change. I also tried manually changing the permissions on the /home/.gnome2 folder (as that was the error I was getting) and again, no luck.

Reinstalling Feisty would not be the worst thing. The only problem is that now XP--which could previously read and write to my Feisty drives--thinks my Feisty drives are not formatted (so I cannot backup my most-recent data).

Again--can anyone help me? Is there an easy way to restore the /home folder (and all its subfolders and files) permissions to default? --Thanks

---

### Post by brion@cbkidder.com on 2007-06-21
Ricardisimo, I was having the same .dmrc problem as hoarsecourser (poster of this thread), and your solution worked like a charm. Thanks a million!

---

### Post by Bill Statler on 2007-06-21
Here's an old thread with some discussion of .dmrc permissions problems:

[*Error on login about .dmrc file permissions?*]("http://ubuntuforums.org/showthread.php?p=437911#post437911")

I don't know if this will solve the specific problems that people are posting here, but it might be worth a look.

---

### Post by Brian96 on 2007-06-22
> **Bill Statler said:**
> Here's an old thread with some discussion of .dmrc permissions problems:

[*Error on login about .dmrc file permissions?*]("http://ubuntuforums.org/showthread.php?p=437911#post437911")

I don't know if this will solve the specific problems that people are posting here, but it might be worth a look.

Thanks, Bill. I think I'm too far gone now to avoid reinstalling, but if I run into this again I think your post will be very helpful.

---

### Post by ahoman66 on 2007-06-22
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

I got the same problem, I believe was caused when I installed conky. **You da man ricardisimo**!

Thank you very much
Allen

---

### Post by sheilnaik on 2007-06-24
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

This worked perfectly!  I accidentally chmod'ed my entire home directory to 777 (don't ask why..), and this fixed it.  Thanks!

---

### Post by pbhill on 2007-06-25
I have the exact same problem as Brian96. Just kept getting deeper and deeper until the only way out seemed to be a clean reinstall. However, even after reinstalling I get the same error message after login "$HOME/.dmrc file is being ignored.."  . How can this be? Am I trapped in limbo destined to repeat my past forever and ever? Help!

---

### Post by lemmy999 on 2007-08-03
Ricardisimo- thank you!!

another user facing .dmrc hell has been saved!!

---

### Post by hamstersquasher on 2007-08-04
I am having this same problem too...

I recently set up my ubuntu machine to dual boot with fedora core (ubuntu is much better).  i thought it would be cool to share the same home folder and I mounted my ubuntu partition and linked my home to my ubuntu home.  I also (REALLY STUPID) changed permissions on my ubuntu partion to 777 and made root owner of everything so I could read my new fedora home directory.  It was a battle just to get X running again on my ubuntu partition.  My concern is that my whole filesystem's permissions are way out of wack and I don't know if it is possible to repair this or should I just reinstall??  thanks in advance

---

### Post by bodhi.zazen on 2007-08-04
> **hamstersquasher said:**
> I am having this same problem too...

I recently set up my ubuntu machine to dual boot with fedora core (ubuntu is much better).  i thought it would be cool to share the same home folder and I mounted my ubuntu partition and linked my home to my ubuntu home.  I also (REALLY STUPID) changed permissions on my ubuntu partion to 777 and made root owner of everything so I could read my new fedora home directory.  It was a battle just to get X running again on my ubuntu partition.  My concern is that my whole filesystem's permissions are way out of wack and I don't know if it is possible to repair this or should I just reinstall??  thanks in advance

Reinstalling is in your future ...

It is very difficult and time consuming to reset all the necessary permissions on the Ubuntu file system.

---

### Post by jambarama on 2007-08-07
> I still have a few questions about this:
1. Why does non-root Nautilus have options for changing permissions if they won't work?
2. Why does root-Nautilus have options for changing permissions if they don't work properly?
3. Is this a Gnome issue (my guess) or linux-image issue?
4. Is this one of those annoying little blips, like the fake error message one gets when going sudo in Nautilus, that is simply not on anyone's radar for getting fixed ever?
Just curious. Thanks again.

I can help with a few of these.  
1 - it is pretty hard to know what will work and what won't.  I've been lurking these forums long enough to see some of the kludges people will do to get things to work (when Compiz/Beryl were new, those were some nasty kludges).  The other thing is freedom, I don't want my OS to tell me what I can do, but you are right--it'd be awfully nice if the system could say "hey, this will probably break X, are you sure".  
2 - see above
3 - This is a linux issue, [this poor guy ]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/35377-can-you-reset-directory-permissions.html")wrecked the permissions on his entire system.
4 - I don't think we can fix this issue.  It is really a matter of education, though a warning would be helpful (if very difficult to code).

---

### Post by jambarama on 2007-08-07
> Can anybody help me? 

I was having the .dmrc being ignored error, so I used these instructions to fix it (except I used 644 permissions instead of 700). Then I got past the login screen without error, but I started getting the "your session lasted less than 10 seconds" error. The output file said it could not create the /home/.gnome2 directory.

Well, I got in this mess--I think--because when I first started in Ubuntu a couple of months ago I wanted to share data between XP and Feisty, so I created a couple of folders. But before I learned to change permissions on folders, I had moved these folders into the /home directory. When that didn't do everything I wanted I started changing permissions. Everything worked fine--except the .dmrc error after login.

Because when I manually changed permissions for my home folder I had ticked the option for applying the changes to all files in the directory, I re-ran the second two commands above with -hR. This also made no change. I also tried manually changing the permissions on the /home/.gnome2 folder (as that was the error I was getting) and again, no luck.

Reinstalling Feisty would not be the worst thing. The only problem is that now XP--which could previously read and write to my Feisty drives--thinks my Feisty drives are not formatted (so I cannot backup my most-recent data).

Again--can anyone help me? Is there an easy way to restore the /home folder (and all its subfolders and files) permissions to default? --Thanks

You aren't in bad shape, no worries.  At the login screen press ctrl-shift-F1 to get to tty1.  Login with your normal credentials and run the commands ricardisimo figured out.  That should work.  If everything is still borked, [first reset the home directory permissions]("http://bbs.archlinux.org/viewtopic.php?pid=20861"), then redo the commands ricardisimo figured out.

---

### Post by jambarama on 2007-08-07
> I recently set up my ubuntu machine to dual boot with fedora core (ubuntu is much better). i thought it would be cool to share the same home folder and I mounted my ubuntu partition and linked my home to my ubuntu home. I also (REALLY STUPID) changed permissions on my ubuntu partion to 777 and made root owner of everything so I could read my new fedora home directory. It was a battle just to get X running again on my ubuntu partition. My concern is that my whole filesystem's permissions are way out of wack and I don't know if it is possible to repair this or should I just reinstall?? thanks in advance.

Go ahead and re-install, but if you are going to share home folders (kind of dangerous but doable) put /home on a separate partition.  Then if this happens again (heaven forbid), you can reinstall the OS(s), without losing the /home config stuff, and you can reset the /home directories as I explained in the post just previous to this one.

---

### Post by Fraoch on 2007-08-11
For some reason setting .dmrc 644 doesn't work for me.  The only way I can get rid of this nag screen is 600.  Perhaps that breaks things, but judging by the content of the .dmrc file:

```
[Desktop]
Session=default
```

I probably don't need it in my setup - I guess it has something to do with multiple users/desktops/workspaces which I don't play around with anyway.

I also have to have my /home/me set 744.

This all starts because I like to share my /home/me directory under samba, which means I have to alter the /home/me directory permissions.  Sharing /home/me under samba is probably also not recommended, but the fact is, if I want a file, it's always in the /home/me directory of my machines.

---

### Post by lanroc on 2007-08-27
Thank-you. I tried several of the other similar solutions offered on line. Yours was the only one complete enough to work in its entiretly. Being quite the newbee, how do you come up with the numbers 644 700 etc for the permissions?

---

### Post by bodhi.zazen on 2007-08-27
> **lanroc said:**
> Thank-you. I tried several of the other similar solutions offered on line. Yours was the only one complete enough to work in its entiretly. Being quite the newbee, how do you come up with the numbers 644 700 etc for the permissions?

See these links :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by macosxistheultimate on 2007-08-28
someone please tell how to boot into recovery mode i have no idea how to i need complet instructions.

---

### Post by Dr Small on 2007-08-28
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=535555](http://ubuntuforums.org/showthread.php?t=535555)

---

### Post by zammtronic on 2007-10-17
Hey All

I had this problem occur when I set up a Feisty box on a corporate LAN, configured with autofs to mount network drives and import the $HOME directory of the user logging in (this machine could, in effect, have infinite users). 
Since most of the users on the network are native to Solaris environments, a .dmrc file does not even exist. If anyone could perhaps tell me what should be in this file I'd greatly appreciate it!

---

### Post by apple_and _linux on 2007-10-24
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

Cool!  You saved my neck!  This happened to my admin account and I was getting super worried.  This exact code worked.  Thanks a million!

---

### Post by herbster on 2007-10-27
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

This JUST happened to me (again) and I found this thread. Ricardisimo you're a stud dude, that fixed everything. Just when I thought I'd have to reinstall *again*!! Props, you've helped a bunch of us here with that, and I've printed it out should it ever happen again. I'm also going to do some studying on permissions now ;)

Thanks again!!

---

### Post by kreuelt on 2007-11-10
Help! I removed the option for booting in restore mode from my GRUB file. How do I fix that? (something as simple as someone else posting what that entry in the list file should look like would help.)

---

### Post by herbster on 2007-11-10
> **kreuelt said:**
> Help! I removed the option for booting in restore mode from my GRUB file. How do I fix that? (something as simple as someone else posting what that entry in the list file should look like would help.)

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a3889ed1-1210-4cd5-8fc4-9309ba6039fc ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot
```

That's mine. Of course, substitute your drive path where mine are (hd1,1 and /dev/sdb2).

---

### Post by PhillipJ on 2007-11-11
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
 things that fix things from a couple pages back
```



i resized my bootable Ext3 partition and got the same error, your suggestions fixed it, thanks :-)

---

### Post by Felipe Butcher on 2007-12-28
Using this you will change permissions of all your home files, your public_html folder will not work inside apache, you will change for 700 files that don`t have to be 700... think two times before doing this.

> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

---

### Post by skat3h3ll on 2008-01-02
super thumbs up sx66gns  u saved me thanks alot!

---

### Post by ClarkePeters on 2008-01-12
> Originally Posted by ricardisimo  View Post
OK. It's been fixed. Here's how:
Code:

```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```

You substitute your user name with mine, of course

Great Job! Another save!  I had tried several other threads, and this worked like a charm first time out!

---

### Post by SPr on 2008-01-13
> **Felipe Butcher said:**
> Using this you will change permissions of all your home files, your public_html folder will not work inside apache, you will change for 700 files that don`t have to be 700... think two times before doing this.

I have this .dmrc problem and would like to know what are the implications of chmodding the entire /home folder to 700?

If it makes any difference this computer is not on a network and has only one user.

---

### Post by ricardisimo on 2008-01-14
If you're the only user, then 755, 766 or even 777 is probably fine. As you yourself quoted, it's been suggested that some apps might not function properly without more "open" permissions. Personally, I'm not sure I like that, even if it's true; why does any app need access to my .dmrc file?

To answer your question, and for whatever it's worth, I set my home folder to 700, and I have yet to run across any problems whatsoever resulting from this. And remember, in linux pretty much every app **has** to access your home folder to personalize its setup and operation for you. It's just a question of what sort of access you allow.

---

### Post by steveneddy on 2008-01-20
> **ricardisimo said:**
> If you're the only user, then 755, 766 or even 777 is probably fine. As you yourself quoted, it's been suggested that some apps might not function properly without more "open" permissions. Personally, I'm not sure I like that, even if it's true; why does any app need access to my .dmrc file?

To answer your question, and for whatever it's worth, I set my home folder to 700, and I have yet to run across any problems whatsoever resulting from this. And remember, in linux pretty much every app **has** to access your home folder to personalize its setup and operation for you. It's just a question of what sort of access you allow.

I thank you for this and the first post you made on this thread about chmod my $HOME folder and the ./dmrc file. I wasn't able to thank you by the thanks button on the first post.

Thank you again for your help.

:popcorn:

---

### Post by SPr on 2008-01-26
Ok,

I decided to wait and think before trying the chmod 700 ~/everything fix.

Then I had a brain wave :) I opened Nautilus, put the side pane to display the tree view, right clicked "Home Folder" in the tree view and changed the permissions to those in the screenshot. I clicked "apply permissions to enclosed file" but I don't know whether or not I should have done. Looking at the permissions in my home folder the files and folders have different settings.

This fix worked for me without the need of changing the permissions of everything in my home folder.

(I blanked out my name in the screenshot.)

---

### Post by ricardisimo on 2008-01-28
> **SPr said:**
> Ok,

I decided to wait and think before trying the chmod 700 ~/everything fix.

Then I had a brain wave :) I opened Nautilus, put the side pane to display the tree view, right clicked "Home Folder" in the tree view and changed the permissions to those in the screenshot. I clicked "apply permissions to enclosed file" but I don't know whether or not I should have done. Looking at the permissions in my home folder the files and folders have different settings.

This fix worked for me without the need of changing the permissions of everything in my home folder.

(I blanked out my name in the screenshot.)

Maybe they've made changes to Nautilus in Gutsy about which I haven't heard, but if you're on Feisty (or any other release) you're going to get the same error messages as everyone else. But please do ease our suspense... how did it go?

---

### Post by SPr on 2008-01-28
> **ricardisimo said:**
> Maybe they've made changes to Nautilus in Gutsy about which I haven't heard, but if you're on Feisty (or any other release) you're going to get the same error messages as everyone else. But please do ease our suspense... how did it go?

I'm on Gutsy and what I did has fixed it. Sorry if I didn't make that clear.

I no longer get the error and everything works well. I have shut down and rebooted and logged out of my account and logged back in a few times to test it and it's fine.

I just wish I knew what caused it.

---

### Post by fatdadkev on 2008-01-28
I had this error after installing "Timevault".
Everything was fine until I activated the program and it started to track file changes.
I rebooted and got the error.

In the end I had to start a terminal session only, manually remove Timevault and purge it out (Using sudo command) then the only instruction that seemed to work was setting the $home directory to 700 permissions.
I then issued a reboot and after it thought about it for a few moments I got straight in, had a few minor tweaks as it appears some things like window positions were not saved when it shut down -  then had to check ownership of the directory and change it back to read/write etc.

The tips really helped and going through them you find one that works for you, I had visions of a re-install but its all going fine - and I've bitten the bullet and done several HARD boots i.e full power down.

Timevault was the only program I had installed and looking at some other threads it looks that it ran and changed file permissions to root rather than for my user, this messed it all up when I booted.

I guess I'll be giving Timevault a miss for a bit ...

---

### Post by Minguo on 2008-01-29
I was having this problem, and while I no longer get the message, things are definitely not fixed.

Here's the story.  I was trying to install a game, Beyond the Redline, but the run package I downloaded wouldn't execute.  I got on the forums and found this thread.   [http://ubuntuforums.org/showthread.php?t=442752](http://ubuntuforums.org/showthread.php?t=442752)   I executed the code in this post: [http://ubuntuforums.org/showpost.php?p=4215678&postcount=6](http://ubuntuforums.org/showpost.php?p=4215678&postcount=6)

Now let me be very clear, I am a Linux newbie, only using for about a month and a half, so I'm not very confident with the terminal yet.  I just* copied and pasted *the code from the post I linked, after the first bit the terminal displayed hundreds of lines, some of which generated errors.   (Probably should've sent up warning flags, but like I said, newb.)  So after that, the binary starts, but the game doesn't function correctly.  Thinking like a windows user I rebooted just for kicks and upon log in, get the **.dmrc file is being ignored **message.   For some reason, my internet won't work and I can't transfer files to my usb key, or mount my NTFS external harddrive.  

So I get on my old windows machine and find this thread.  I follow the instructions ricardisimo posted, which gets rid of the **.dmrc file is being ignored **message, but internet still doesnt work and file access is screwy.  I then followed the directions that Jambarama posted about resetting the home directory and redid the ricardisimo fix, still no help.   

At this point, I think I'm going to just re-instal.  However, I'd like to know why the seemingly innocuous code from the Beyond the Redline thread nuked my system?  Let me repeat, I copied and pasted the bolded lines of terminal commands (without the parenthesis)  What happened?  Here's the code if you don't want to click the link.

> sudo chmod 777 -R / /usr/local/games/btrl_demo/
> sudo chmod 777 -R .btrl_demo

---

### Post by ricardisimo on 2008-02-05
```
sudo chmod 777 -R / /usr/local/games/btrl_demo/
sudo chmod 777 -R .btrl_demo
```

Odd... that code doesn't seem to affect your Home folder at all, so I'm at a loss to explain your troubles. Without knowing any other details, I'd have to guess that you have had an experience similar to about a dozen that I had in my first year as an ubuntite; namely, sheer coincidence. I can't tell you the number of times I clicked on some link, only to have my connection drop, or I installed some program and my sound or graphics would go screwy.

Right this very moment I'm having that issue on my home compootor, where I tried upgrading to Gutsy, only to have my motherboard start hiccuping. It's just coincidence, though. Only very recently am I starting to understand - somewhat - the logic involved, and what are the likely culprits and what aren't. If I were a betting man, I'd say something else was at fault (or at least not specifically those two lines of code). Anyhow, sorry you're having troubles. I hope it's been resolved.

---

### Post by bodhi.zazen on 2008-02-05
The very first command, 

> sudo chmod 777 -R / /usr/local/games/btrl_demo/ is the culprit.

It changed the permissions of your entire install. This command can be broken into two to understand :

sudo chmod 777 -R / # <- This command affects your entire install, icluding /home
sudo chmod 777 -R /usr/local/games/btrl_demo

In my experience it is next to impossible to recover after changing your permissions to 777, and when possible it takes longer then re-installing.

My advice is to re-install. It is a hard lesson to learn, but you have to be very careful with sudo and the recursive flags (-r or -R).

---

### Post by Chudilo on 2008-03-04
It would not work for me until I set permissions to 755 on my user directory recursively.
(including .dmrc)
I think it's reasonable to leave permissions at 755.

---

### Post by seh87 on 2008-03-26
Thanks!  You all have been very helpful!
:)

---

### Post by Kokesh on 2008-04-04
Can you see that in nautilus with "Show hidden files! " option? It is hidden file.

---

### Post by ricardisimo on 2008-04-06
> **Kokesh said:**
> Can you see that in nautilus with "Show hidden files! " option? It is hidden file.

I'm not sure to what you are referring, but I've been led to believe that Hardy functions a bit differently with regards to Nautilus and the .dmrc file. Much of the above might not apply to you.

---

### Post by cygnus-X1 on 2008-05-02
I just started using/learning Ubuntu 8.04 Hardy Heron within the past 3 days. So I'm new to this gig. (Bye-bye Billy G.!) The 644 error message popped up shortly after I got most everything configured at the most basic level. Sure, I could do it the *easy* way and reload. But then what would I learn from that? I had a little experience with Unix back in the early 90s, so I can at least somewhat understand the Linux lingo. 

I don't know much about Nautilus, so I tried ricardisimo's formula in terminal using both the sudo and gksudo commands. Sudo wouldn't give permission for the -r 700 command and gksudo said the -r wasn't an option. I rebooted and fired up the recovery mode. Then entered in the four commands. Viola'! Problem fixed! Now if I can find out what caused the problem in the first place, that would be great. Many thanks ricardisimo! 

BTW - Me and most of my associates agree with your iii's! ~_o  
      The truth IS out there...

___________________________________________________________________________________
To err is human. To really screw things up takes W!nd0$$$$... Dang, it broke again!

---

### Post by pro003 on 2008-05-04
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

thanks buddy - this just solved my problem in ubuntu 8.04 :)

---

### Post by talking Llama on 2008-05-08
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.
I was having the same problem as hoarsecourser but ricardisimo's method got rid of the warning message. Thanks very much ricardisimo! :D

---

### Post by dcfmarcos on 2008-05-09
For people having problem in the log in 10s. I log in from terminal safemode and use gksudo nautilus command. Browese to home/username go to propertis then permissons,in the part of other put none for folder accses and file acsses. Then I could log in without the 10s log in and .dmrc ignored.

---

### Post by grantbey on 2008-05-10
Read through all of this post and nothing has worked for me. I've tried the chmod and chown commands as supplied, even from recovery mode and nothing seems to work.

Perhaps the background will help to elucidate a solution; I moved the home directory to a separate partition so that the files would be accessible from both windows and linux. The partition is NTFS - could this hold the same inherent problems that some users mentioned about FAT32 with regards to unsupported permissions?

Help would be much appreciated!

Grant

---

### Post by bodhi.zazen on 2008-05-10
> **grantbey said:**
> Read through all of this post and nothing has worked for me. I've tried the chmod and chown commands as supplied, even from recovery mode and nothing seems to work.

Perhaps the background will help to elucidate a solution; I moved the home directory to a separate partition so that the files would be accessible from both windows and linux. The partition is NTFS - could this hold the same inherent problems that some users mentioned about FAT32 with regards to unsupported permissions?

Help would be much appreciated!

Grant


NTFS is not a linux native file system. Although you can read/wirte to NTFS partitions you can not install linux into them or mount them as /home.

You will need to move /home back to a linux native file system, and all your permissions may well be off, it may be you will need to fix a number of permissions....

---

### Post by biddumehta on 2008-05-11
I am stuck up at logon -  $HOME/.dmrc file is being ignored

I have tried all the possible methods ..

Can someone save me from Re-install of UBUNTU .

---

### Post by grantbey on 2008-05-11
Thanks bodhi.zazen, I had been fearing as much.

I've unmounted the NTFS drive, replaced the old home directory as it was and I got the permissions back so everything is now normal. Now I'm going to try to mount the same drive into /home but I'll format it as ext3 first. 

The next question is will windows be able to access all the files? We're spending so much time on all these permissions so won't I be locking myself out of my own personal documents when I'm not using ubuntu?

---

### Post by siafulinux on 2008-05-11
Hello everyone

I awoke this morning to the same problem... during boot power was brought down by a thunderstorm, but came back immediately. I assume this was the problem. Sorry, I didn't write any of the actual error messages down.

Rebooted and the .dmrc error occurred. Ended up doing the following to correct:

[LIST=1]
[*]sudo chmod 644 /home/[username]/.dmrc
[*]sudo chown [username] /home/[username]/.dmrc
[*]sudo chmod 755 /home/[username]
[/LIST]

I then ended up with another login error about being unable to create a file in the /tmp/ directory and that there were "too many links". 

[LIST]
[*]sudo rm -r /tmp/*
[/LIST]

Was able to log in per normal.
Hope this helps someone!

JC

---

### Post by bodhi.zazen on 2008-05-11
> **grantbey said:**
> Thanks bodhi.zazen, I had been fearing as much.

I've unmounted the NTFS drive, replaced the old home directory as it was and I got the permissions back so everything is now normal. Now I'm going to try to mount the same drive into /home but I'll format it as ext3 first. 

The next question is will windows be able to access all the files? We're spending so much time on all these permissions so won't I be locking myself out of my own personal documents when I'm not using ubuntu?

Well you have a few options. First is a shared data partition, it can be NTFS and both Ubuntu and Windows can rw ntfs. IMO this is the best option.

You can then link your data to home :

ln -s /media/data /home/user_name/data

Just do not mount the data partition as /home Besides, there are a number of files and directories (configuration files) you do not need access to from windows ....

To understand permissions :

 [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Permissions are a little strange at first but once you understand them you will learn to love them.

An alternate is to install a driver in Windows :

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

This driver seems reasonable but may not be as reliable as the ntfs driver on Linux (ntfs-3g).

---

### Post by vprasaj on 2008-05-23
> **biddumehta said:**
> I am stuck up at logon -  $HOME/.dmrc file is being ignored

I have tried all the possible methods ..

Can someone save me from Re-install of UBUNTU .

Post #8 is the solution. No need to reinstall.

---

### Post by larryhaja on 2008-05-26
> **siafulinux said:**
> Hello everyone

I awoke this morning to the same problem... during boot power was brought down by a thunderstorm, but came back immediately. I assume this was the problem. Sorry, I didn't write any of the actual error messages down.

Rebooted and the .dmrc error occurred. Ended up doing the following to correct:

[LIST=1]
[*]sudo chmod 644 /home/[username]/.dmrc
[*]sudo chown [username] /home/[username]/.dmrc
[*]sudo chmod 755 /home/[username]
[/LIST]

I then ended up with another login error about being unable to create a file in the /tmp/ directory and that there were "too many links". 

[LIST]
[*]sudo rm -r /tmp/*
[/LIST]

Was able to log in per normal.
Hope this helps someone!

JC
I did as **siafulinux** posted and it worked form me.  Thanks for the solution.

---

### Post by acmal on 2008-05-26
my home is empty, so when i do:

chmod 644 /home/acmal/.dmrc >>> no such file or directory

then i just do:

chmod 644 /home , and it solved :-)

---

### Post by noesquire on 2008-06-01
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```

Thanks. I was tinkering with permissions using gksudo nautilus when I lost control of a **lot** of things. Heart skipped a few beats when my Vista dual-boot also had a couple of failed boots [unrelated obviously]. So thanks for providing the solution when I was finally able to get online.

---

### Post by Kuroda_Shun on 2008-06-03
Thanks ricardisimo, and thanks Ubuntu forums :)

---

### Post by se user on 2008-06-26
> **ricardisimo said:**
> OK. It's been fixed. Here's how:
```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

Is there anyway to make your /home folder utterly invisible to other users (beside owner and root, of course)? In other words, not only can they not open it, they can't even find it. Just curious, because I remember a similar option in Windows.

Thankyou so much you saved my life (well my pc's life anyway) thanks again

---

### Post by erhabener.meister on 2008-06-26
I only had to click right on my home folder and change the options into this:

_Owner_
Folder acces: create and delete files
file ascess:read and write

_Group_(=username)
Folder acces: create and delete files
file ascess:read and write

_Others_
Folder acces: access files
File access: read-only

---

### Post by ricardisimo on 2008-06-29
> **erhabener.meister said:**
> I only had to click right on my home folder and change the options into this:

_Owner_
Folder acces: create and delete files
file ascess:read and write

_Group_(=username)
Folder acces: create and delete files
file ascess:read and write

_Others_
Folder acces: access files
File access: read-only

So it's true... Hardy has worked out some of these problems with Nautilus? (I'm still on Feisty at home, and Kubuntu Hardy here, so... )

---

### Post by isaiah55 on 2008-07-09
Ricardisimo, I was having the same .dmrc problem as hoarsecourser (poster of this thread), and your solution worked a treat - thank you very much

---

