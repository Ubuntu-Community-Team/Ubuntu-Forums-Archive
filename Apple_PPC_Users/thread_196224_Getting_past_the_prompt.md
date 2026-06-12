---
title: "Getting past the prompt"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by VittorioCole on 2006-06-13
I've just installed Ubuntu 6.06 on my mac, and when it boots, rather than getting a GUI, i stay at the prompt. I remember in suse, all i had to do was log in as root, and type "init runlevel 5" but that doesnt seem to work here. 

What can i do to get my GUI?:confused:

---

### Post by BoneKracker on 2006-06-18
It should have automatically booted you into the GUI.  The default install has X, gdm, gnome-session, and everything all set up.  In fact, you have to take special action NOT to boot into the gui.  Are you doing anything at the boot prompts besides just hitting return to accept the default boot?

How did you install?  Did you install the **server** or something?  I don't believe the server installs gui by default.  If so, you can add it with:
```
sudo apt-get install <package>
```
where <package> is the gui bundle you want (e.g. "gnome-desktop")

Once you have the gui, explore the menu "System > Help" to see what's different about ubuntu.

For example: Ubuntu does not use the same default runlevels as Suse.  Also, ubuntu is set up with the assumption that you will NOT log in as root (that you will use sudo).  Sudo is also set up by default for the first "normal" user during the installs, unless you install server in the expert mode (I believe).  Some of the groups are different.  Oh, and you don't have to pay for updates.

---

### Post by VittorioCole on 2006-06-23
I'm not sure if i installed the server or just the regular edition. Is there an easy way to check this from where i am?

---

### Post by scxtt on 2006-06-23
try:```
startx
```

---

### Post by BoneKracker on 2006-06-24
uname -a

---

### Post by scxtt on 2006-06-24
[QUOTE=BoneKracker]uname -a[/QUOTE]wouldn't that imply that my "desktop" (installed via the alternate CD) would tell me that? -- cause it doesn't ...```
:> uname -a
Linux madiera 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
```

---

### Post by VittorioCole on 2006-06-24
Alright, i've found out that i've downloaded the Server edition on mistake, but i'm just going to keep it, and use that.. 

I'm using the Ubuntu Alternate disk to install Gnome, and hopefully, that will be problem solved for me. :)

---

### Post by BoneKracker on 2006-06-25
scxtt,

I can tell you installed the desktop version because your kernel is labeled "PREEMPT".   The server version has a different name.

They labeled it that way because it is configured to use a preemptive model of multitasking, which is not appropriate for most servers and is a change to how the old desktop kernel was configured.  In theory it should make it more responsive to user-generated input.    Because of this naming, uname was a quick way to tell what he installed.

Trying startx was a good idea but not called for because we already know X isn't working -- his question was why.  It could have been for some other reason, but as I suspected, he installed the server version.

---

### Post by BoneKracker on 2006-06-25
Vittorio,

If you've got the server edition up and running, and you have a broadband internet connection, you could install Gnome via the terminal:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop

```

It does run fine as a desktop.  I can't tell the difference.

---

### Post by VittorioCole on 2006-06-25
I tried this, only using the Alternate CD instead of a broadband connection. It lists all the things it will install, and this will require 1347MB additional space and all that jazz. 

When i type "y" to continue, it stells me alot of 
"Buffer I/O error on device hdb, logical block xxxxxxxxx" with the x's replaced with numbers.

After a while, it installed files, and said it was all installed, but i tried 

sudo /etc/init.d/gdm start

but it told me the file or directory does not exist.. 

Any ideas, such as bad burn? I'm thinking that's not it because of the "hdb" text in the error message. :\

---

### Post by scxtt on 2006-06-25
[QUOTE=BoneKracker]I can tell you installed the desktop version because your kernel is labeled "PREEMPT".   The server version has a different name.[/quote]yeah, i had a feeling the "preempt" would mean something like that - what does the server version say?[QUOTE=BoneKracker]Trying startx was a good idea but not called for because we already know X isn't working -- his question was why.  It could have been for some other reason, but as I suspected, he installed the server version.[/QUOTE]up to that point, the only question he had was "which version did i install?" -- not being able to start x (or not getting a GUI upon boot) would be a good indication of which version was installed since the server version wouldn't have the facilities to "startx" ... but it's a moot point now ...

---

### Post by BoneKracker on 2006-06-26
You might have bad blocks on your hard disk.

Hopefully other people will chime in with what other issues might produce that error message.  Maybe scxtt has some better ideas.

Here are my suggestions based on the possiblity of disk issues.

1.  Try it again.
If you get the same error, drop into the shell (a menu option in the alternate installer) and do a filesystem check on that partition.```

man fsck
fsck /dev/hdb#
```(man will educate you about fsck.  Replace # with the partition# in question)
After the fsck, resume where you left off.

2.  If that doesn't work, back up in the install process to before the partitioning and repeat the partititioning (or just start the install over).

3.  If you are still getting the same errors, check the disk out with a utility from your drive manufacturer.  Go to their web site.  Don't rely on S.M.A.R.T., do an actual zero-write test if you can.

---

### Post by scxtt on 2006-06-26
[QUOTE=VittorioCole]When i type "y" to continue, it stells me alot of 
"Buffer I/O error on device hdb, logical block xxxxxxxxx" with the x's replaced with numbers.[/quote]the 1st time i decided to use Dapper (i was VERY content w/ my Breezy install, but i did want a shiny, new Dapper) i did an upgrade, got errors just like that as well as an alert box telling me an icon was missing [ about 100 times ] ... honestly, i think the upgrade process doesn't work well - it's a great concept, but i trust a fresh Dapper install much more ... i think it's something you should consider [i.e. don't use the server disk, but get an Alternate disk and install from that ] ... an fsck is a great idea, if for nothing else - peace of mind ...

[quote=VittorioCole]After a while, it installed files, and said it was all installed, but i tried 

sudo /etc/init.d/gdm start

but it told me the file or directory does not exist..[/QUOTE]are you sure gdm was installed?  i'd do a "whereis gdm" and see if you get results similar to this:
[indent]:> whereis gdm
gdm: /usr/sbin/gdm /etc/gdm /usr/lib/gdm /usr/share/gdm /usr/share/man/man1/gdm.1.gz[/indent]but you shouldn't need gdm to startx ...

---

