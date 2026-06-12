---
title: "Suddenly Can't Log In"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Geffers on 2006-08-19
I've been running Breezy Badger for a few months with no problem.

Now suddenly I cannot log in as my main originally created user, gnome just blanks the screen then returns me to the login splash screen with no error message.

KDE tells me, Problem detected trying to start - No Write Access to /home/geoff/.ICEauthority

Fortunately I can log in with other created usernames created only for practice with samba but all my original layout is with my main user.

I have not knowingly altered any access permissions but have been having a problem trying to set up samba users and passwords so may have inadvertently altered something.

I'm having a problem now getting root priviledges :mad: although at the moment it appears I can log in to webmin as root.

Any suggestions appreciated at this stage.

Geffers

---

### Post by taurus on 2006-08-19
Boot into recovery mode from GRUB, then run

```

chmod 644 /home/geoff/.ICEauthority

```
Reboot and see if you can log in to geoff this time!

---

### Post by jimbren on 2006-08-19
This is pretty easy to fix.

Log into the console or a failsafe session, and do this from your command prompt:

```
sudo chown yourusername:yourusername **.**
```

Then you can log out ofyour console and log into X normally.

I've found that this happens when I am doing something and improperly start up a program as root, like Nautilus or Konqueror.  Root takes ownership of certain key files, and then you can't write to them when you try to log into your session.

Let me know if that doesn't work.  I run into this question fairly regularly on the forums, and I was kind of thinking of writing a howto on it.  It would be my first...

---

### Post by ComplexNumber on 2006-08-19
the problem is meant to be caused by running graphical applications such as gedit and nautilus etc by using 'sudo'. for example 'sudo nautilus' is not advised. the correct and best way is to use 'gksudo nautilus', and 'gksudo' for all graphical applications(ie applications that use a GUI). 
thats one of the causes of the error anyway, but a common one at that.

---

### Post by Geffers on 2006-08-19
> **ComplexNumber said:**
> the problem is meant to be caused by running graphical applications such as gedit and nautilus etc by using 'sudo'. for example 'sudo nautilus' is not advised. the correct and best way is to use 'gksudo nautilus', and 'gksudo' for all graphical applications(ie applications that use a GUI). 
thats one of the causes of the error anyway, but a common one at that.

Thanks for reminder, I have used sudo quite a bit recently trying to get samba to work.

Geffers

---

### Post by Geffers on 2006-08-19
Thanks Taurus and jimbren, taking your advice I have altered .ICEauthority to 666 and it now works.

I know ubuntu's use of root can be confusing but this ICEauthority file shows as belonging to root whereas all the other user ICEauthority files belong to the specified user.

Obviously it is working as all have read/write access but should I be shown as owner or is this something to do with me being the first created user with root access.

Geffers

---

### Post by Benjward on 2006-08-19
Hi there,

Strangely enough, what sounds like the exact same thing has just happened to me. I'm running Dapper though. I shut the machine down last night, and this morning can't log on (boots back to the login screen).

Needless to say I've tried the above suggestions, but that didn't fix anything. From what I can tell, I already owned everything in my home folder anyway... :(

Any further suggestions?

Thanks in advance guys, much appreciated.

Ben

---

### Post by Benjward on 2006-08-19
Not to worry; I've managed to log in now. After adding a whole new user through the terminal and still not being able to log in, I tried a different approach. I re-installed an older kernel (linux-image-2.6.15-25-386 instead of linux-image-2.6.15-26-386) which seems to work.

Not sure what's wrong with the newer one... that's for another day! :)

Ben

---

### Post by taurus on 2006-08-19
> **Benjward said:**
> Not to worry; I've managed to log in now. After adding a whole new user through the terminal and still not being able to log in, I tried a different approach. I re-installed an older kernel (linux-image-2.6.15-25-386 instead of linux-image-2.6.15-26-386) which seems to work.

Not sure what's wrong with the newer one... that's for another day! :)

Ben
I guess the moral of the story is the latest is not ALWAYS the best...  ;)

---

### Post by jimbren on 2006-08-21
Are you using proprietary video drivers for an Nvidia or ATI card?  If so, I've seen entries in the forums referring to having a similar problem to this after updating to a newer kernel. You have to re-apply the drivers, I believe.  

Search around and you'll find it...

---

### Post by tkirke on 2006-08-21
I'm having the same problem...
Old kernels don't help, new users don't help.
What can I do, short of re-installing?

---

### Post by jimbren on 2006-08-21
When you try to take ownership of all files, what happens?
```
sudo chown yourusername:yourusername *.*
```

---

### Post by jtrompe on 2007-05-18
I'm having this exact problem and none of the solutions offered here worked for me.  any other ideas?

---

### Post by icechen1 on 2007-05-18
This might help
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by dannyboy79 on 2007-05-18
just an FYI for everyone. this is the same result that will occur when there is NO ROOM to write the files needed to start the machine. this happened to me on a laptop which had really no room for downloading and compiling stuff so after I shut it off, my home directory was 100% and I couldn't log in. all I had to do was just deelte a few things and I could log back in.

---

### Post by jtrompe on 2007-05-18
> **dannyboy79 said:**
> just an FYI for everyone. this is the same result that will occur when there is NO ROOM to write the files needed to start the machine. this happened to me on a laptop which had really no room for downloading and compiling stuff so after I shut it off, my home directory was 100% and I couldn't log in. all I had to do was just deelte a few things and I could log back in.

Although I too had a full hard drive, after deleting several hundred megs of files I still could not log in.

---

### Post by jtrompe on 2007-05-18
> **icechen1 said:**
> This might help
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

I just checked out that link and I'd like to give it a try but I use kde.  could you tell me the equivalent files to remove?  I would ask on the other site but I don't have an account there.

---

### Post by dannyboy79 on 2007-05-18
do you have a seperate home partition or not? if you have a seperate home partition and you deleted file from anyplace other then your home partition, this still won't work.

---

### Post by jtrompe on 2007-05-18
I went ahead and tried to delete the files listed to restore defaults and that didn't resolve the problem.

when I was in console mode I tried to open a man page and I got the error "gzip: stdout: No space left on device" but as far as I can tell there is at least 200 mg left on the drive.

---

### Post by taurus on 2007-05-18
Boot into recovery mode from GRUB menu and run

```
aptitude clean
df -h
```
Post the output of the second command here.

---

### Post by jtrompe on 2007-05-18
> **taurus said:**
> Boot into recovery mode from GRUB menu and run

```
aptitude clean
df -h
```
Post the output of the second command here.

I'm going to boot back to ubuntu and give this a try.  for some reason my internet connection is bound in some way to successfully logging in to the window manager.  back when I could load into it I could connect in console mode with links but this is no longer possible.  not sure how to save the output, I am that unschooled at this, but i have pen and paper.  brb

---

### Post by dannyboy79 on 2007-05-18
if he can't even open a man page, his drive is definitely full. he needs to clean out some space for files to be written to his home partition and now it sounds like his root partition.

---

### Post by jtrompe on 2007-05-18
it says that my root partition has 27 out of 28 gigs used, and is at 100%, but that 100% is just because it's rounded off.  I can create files.  is there some simple command that just prints how much free space there is on the drive?  when the gui drops out from under me I'm in big trouble.  I can't even figure out how to use the | correctly

---

### Post by jtrompe on 2007-05-18
I'm back in windows now and have a driver that let's me read the filesystem.  I did not install this driver until after my window manager locked me out so it's not the cause of the problem.  I can see files from windows so if there are any questions I can answer from here it is much easier for me to do.

---

### Post by dannyboy79 on 2007-05-18
your ROOT partition says you have a 1 gb left, and what about your home partition?

I beleive df- h will show you in the second or third column teh amount of kb or mb that is left. I know there's a column that shows you percentage, but I thoguht there was another column also.

---

### Post by jtrompe on 2007-05-18
WOOOOOOP  I'm back in the game!  Cleared up a much larger chunk of space and it worked.  I deleted all of my configuration files but whatever.  I new day has dawned.  thanks very much for your patience.

---

### Post by dannyboy79 on 2007-05-21
this happened to me this weekend, it turned out the xorg.conf I copied from another forum user thru IM had the incorrect keyboard layout so despite me entering in my username and password over and over it kept saying I was entering the wrong password and or username. I guess this is differnet than your case because your's actually appeared like it was going to make it but then it would take you back to the login screen. The other thing that was occuring was that my wireless keyboard was dying also, so even though I thought I was entering the right password and or password, a letter was not being registered here and there so that and the combination of the wrong keyboard layout were the causes. just an FYI for everyone.

---

