---
title: "Installing software (Lillypond)"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-06-18
Hi,
Lillypond is a music processor.......bit like Open Office, but it writes out music.

Anyway, I tried installing it through Synaptic..it appears to download and install, but then nothing shows in my applications lists.
So I tried downloading it from the website.
Now I've got an icon on my desktop that does nothing.
The website tells me to do this.

sh lilypond-X.Y.Z.linux-64.sh

I try doing that in Terminal, but that doesn't work.
I think I have to add something to the front of sh lilypond-X.Y.Z.linux-64.sh to tell Terminal that the file is on the desktop.....I think.

Any advice and could I be having problems because of my AMD64 processor?
Thanks in advance.
Phil Edwards

---

### Post by avik on 2007-06-18
Use sh ~/Desktop/*<name of .sh file>*

Also, you might have to put sudo in front of it if it says something about insufficient permissions.  If you do have to do this, then when it asks for your password, type it in and press enter.  When you type, nothing will show up, but that is normal.

---

### Post by groeswenphil on 2007-06-19
Well, that appeared to work.

I got this:-



LilyPond installer for version 2.10.25 release 1.
Use --help for help


You're about to install lilypond in /usr/local/lilypond/
A script in /usr/local/bin/ will be created as a shortcut.

Press ^C to abort, or Enter to proceed

Making /usr/local/lilypond/
Creating script /usr/local/bin/lilypond
Creating script /usr/local/bin/lilypond-wrapper.python
Creating script /usr/local/bin/lilypond-wrapper.guile
Creating script /usr/local/bin/uninstall-lilypond
Untarring /home/philip/Desktop/lilypond-2.10.25-1.linux-64.sh
To uninstall lilypond, run

    /usr/local//bin/uninstall-lilypond


For license and warranty information, consult

    /usr/local/lilypond/license/README


Now.......I've found the file where the software installed, but I still can't see an icon under the applications list to start the thing off.

So.........where did I go wrong?

Thanks,
Phil

---

### Post by freesitebuilder on 2007-06-19
I've found two or three programs that don't add themselves to the menu. In Dapper you can use Alacarte to add them, if they show up there.

---

