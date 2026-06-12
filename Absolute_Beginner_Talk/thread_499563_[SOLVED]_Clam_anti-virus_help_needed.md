---
title: "[SOLVED] Clam anti-virus help needed"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-07-12
I installed the Clam anti-virus application only to discover it doesn't work:  There are some data it claims it's unable to access.  Fine, so I went to the recommended web site and found this information:

> NOTE: If you're using Ubuntu, there's no prebuilt ClamTk 2.99 yet. So, do this instead:
1. Download the ClamTk *.tar.gz file by following the "Downloads" link to the left.
2. tar -xzf clamtk-2.99.tar.gz
3. chmod +x clamtk-2.99/clamtk
4. sudo mv clamtk-2.99/clamtk /usr/bin/
That should do it!

Number 1 was easy enough:  The download now sits in my download folder.  However, I've no idea what numbers 2 and 3 mean.

Are numbers 2 and 3 commands which need to be entered via a terminal?  Are they names of files or folders I'm supposed to create -- someplace?

I take it number 4 is a command to be entered via a terminal, but at this point I'm not even sure of that.  Plus, I've no idea how to install all the stuff that's in the compressed folder (number 1 on the above list) as there's no "Install" function to be found.

Mind, I'm not seeking testimonials regarding a lack of need for an anti-virus program.  What I'm looking for is step-by-step advice on how one accomplishes numbers 2 through 4 on the above list -- plus how one installs the contents of the downloaded compressed file.

Thank you very much, whomever you may be, for helping me with this!  Your assistance will be greatly appreciated.

](*,)

=^..^=

---

### Post by Al3xK3aton on 2007-07-12
Eventually they WILL release a pre-built version for ubuntu, so you can probably just wait it out.

---

### Post by p_quarles on 2007-07-12
There's a Debian package available at Sourceforce. I use that, and it works just fine, and Gdebi takes care of the installation. You can find it here:

[http://sourceforge.net/project/downloading.php?group_id=131278&use_mirror=umn&filename=clamtk_2.99-1_all.deb&25731900](http://sourceforge.net/project/downloading.php?group_id=131278&use_mirror=umn&filename=clamtk_2.99-1_all.deb&25731900)

Keep in mind, though, that you won't be able to update the virus database from the graphical application unless you run it with "gksu." I find it easier to open a terminal before running it and typing ```
sudo freshclam -v
```Hope this solves the problem for you.

EDIT: Just realized that the link above goes straight to the download. The project page is here:
[http://sourceforge.net/projects/clamtk/](http://sourceforge.net/projects/clamtk/)

---

### Post by Flyvapnet on 2007-07-12
Thank you for the encouraging news, **Al3xK3aton**!  I shall keep an eye out for the eventual *proper* release.

[-o<

**P_quarles**, I've downloaded that file you mentioned, so now I'll see what happens when I (try to) install it.  But, what's "gksu"?

:confused:

=^..^=

---

### Post by p_quarles on 2007-07-12
Not at all difficult to install . . . just click on it, and select the default (Gdebi) option to open it.

"gksu" is a terminal command that allows you to run graphical applications as root. To use this with clamtk, open a terminal and type ```
gksu clamtk
```

It'll ask for your password, and then you'll be set.

---

### Post by user1397 on 2007-07-12
yep, steps 2 - 4 from the first post *are* terminal commands.

there is no installation -- those commands are the installation

---

### Post by bodhi.zazen on 2007-07-12
> **Flyvapnet said:**
> But, what's "gksu"?

:confused:

=^..^=

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Nice cat ;)

---

### Post by kavon89 on 2007-07-13
Why would you need an anti-virus for Ubuntu? I actually had a hard time getting a virus in Windows. Every time I scan with AVG it comes up with nothing every time, for 2 years, I never had any problems which could be caused by a virus anyway. Granted, I am pretty much a "Windows expert".  Getting Linux viruses should be MUCH rarer than when compared to Windows too.

From what I've learned, the best anti-virus is a smart user. ;)

---

### Post by sab0403 on 2007-07-13
Alright, step by step...

```
1. Download the ClamTk *.tar.gz file by following the "Downloads" link to the left.
```As you said, simple enough, download and that's it.```
2. tar -xzf clamtk-2.99.tar.gz
```This is indeed a comand you have to run in the terminal... what you're doing here is using a package decompressor (think winzip/winrar) to unpackage the installation files. In this case the program is tar, and the -xzf are parameters to define which kind of file you're decompressing (since tar reads many types of files), how to do it and so forth. clamtk[...] is the name of the file you've downloaded.```
3. chmod +x clamtk-2.99/clamtk
```Here you're changing the permissions on the file.```
4. sudo mv clamtk-2.99/clamtk /usr/bin/
```Now you're just moving the file(s) to the /usr/bin location, so you can run them from any terminal at any time (think of this as adding them to the list of commands that the OS understand).

Hope this helps...

---

### Post by sab0403 on 2007-07-13
I didn't explicitly mention this but yes, steps 2/3/4 are commands to execute in the terminal. Also sudo or gksudo means you're running that command *as root*, so you have total permissions.

---

### Post by Flyvapnet on 2007-07-13
Well, I ran that first command and this was the result:

> joseph@joseph-desktop:~$ tar -xzf clamtk-2.99.tar.gz
tar: clamtk-2.99.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
joseph@joseph-desktop:~$ 


Now, I'd already downloaded the relevant file.  It's sitting there, right in my download folder, but somehow it's invisible?

Perhaps the file should have been downloaded to another, more acceptable, location?  I'm totally confused now.

:confused:

=^..^=

---

### Post by p_quarles on 2007-07-13
In the above, it looks like you need to cd (change directory) into your download folder. When you open a terminal, you're in your home folder. 

Did you try installing the package I linked to? It's a fully-functional package for Debian, upon which Ubuntu is based. All you need to do is click on the file, and it takes care of the rest for you. If you got an error, someone might be able to help you with that.

---

### Post by Flyvapnet on 2007-07-13
I'm going to try that package you linked to, **p_quarles**, but first I want to try getting this other thing installed.  If that should prove too problematic, then I'll attempt installing the package you suggested.

Anyway, following your advice but in a different manner, what I did was move the file to my Home directory.  Here's the result:

> joseph@joseph-desktop:~$ tar -xzf clamtk-2.99.tar.gz
joseph@joseph-desktop:~$ chmod +x clamtk-2.99/clamtk
joseph@joseph-desktop:~$ sudo mv clamtk-2.99/clamtk/usr/bin/
Password:
mv: missing destination file operand after `clamtk-2.99/clamtk/usr/bin/'
Try `mv --help' for more information.
joseph@joseph-desktop:~$ mv --help
Usage: mv [OPTION]... [-T] SOURCE DEST
  or:  mv [OPTION]... SOURCE... DIRECTORY
  or:  mv [OPTION]... -t DIRECTORY SOURCE...
Rename SOURCE to DEST, or move SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
  -f, --force                  do not prompt before overwriting
  -i, --interactive            prompt before overwrite
      --strip-trailing-slashes remove any trailing slashes from each SOURCE
                                 argument
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  move all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 move only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
joseph@joseph-desktop:~$ 


Call me Mr. Dumb Guy, because I've spent the past 13 years using Apple and PC operating systems wherein you can simply "Install" things.  Why that user-friendly approach to installation seems to have escaped the comprehension of Linux developers is beyond me; but I'm willing to learn this overly-complicated system,  though it'll take some time.

Anyway, what do I do now?  All I want to know is what code to enter in order to get this anti-virus thing working; and the descriptions of procedure contained in the quote-box above make my head hurt.

Thank you for your patience and understanding!  Personally, I think all this difficulty is Ubuntu's way of punishing me for not having turned to Linux sooner.

:confused:

=^..^=

---

### Post by Flyvapnet on 2007-07-13
**Ubuntuman001**, thank you for your answer to one of my questions!  I'm not the sharpest knife in the drawer, but I'll get the hang of all this -- eventually.

Thank you, **bodhi.zazen**, for that link addressing my question about "gksu"!  Please wish me luck.

**Kavon89**, your points are well taken -- though your last point seems painfully relevant, as I'm not feeling all that smart just now!  Anyway, I'm reminded of some advice I received 39 years ago whilst in the Republic of Viet Nam:  "You don't have to wear your helmet and flak jacket all the time.  The bad guys haven't attacked in weeks.  They've given up bothering us."

Thank you very much, **sab0403**, for your clear guide to carrying out those commands!  I really appreciate your help; and I'm trying as best I can to get this anti-virus package installed, which would be impossible without your advice and that of others.

**P_quarles**, your ongoing advice is most welcome!  Thank you for sticking with me on this problem.

:cool:

=^..^=

---

### Post by Flyvapnet on 2007-07-15
[COLOR="DarkOrange"][SIZE="4"]**Happy ending!**[/SIZE][/COLOR]

\\:D/

I installed Automatix2 and subsequently successfully installed this:

> Build: ClamAV 0.90.2	

Signatures: 104500	
(15 Jul 2007)

GUI Version: 2.32

So it's all good.  Thanks again, folks, for your attention to this problem I was having:  I really appreciate your advice!

:popcorn:

=^..^=

---

