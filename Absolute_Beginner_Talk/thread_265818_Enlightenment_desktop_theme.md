---
title: "Enlightenment desktop theme"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2006-09-26
I was hoping to install Enlightenment, it looks pretty cool, the theme below that is, however I messed around with it a bit last night and got pretty frustrated.  Is there an easy way to do this or a nice theme manager that can allow for transparent windows that ISN'T so complicated to install for a 100% beginner?

[http://themes.freshmeat.net/projects/nix/](http://themes.freshmeat.net/projects/nix/) (them I had hoped to use)

---

### Post by bodhi.zazen on 2006-09-26
Copy your folder with your new theme to your ~/.enlightenment/themes folder. Then, start X11 and in enlightenment 'select' the new theme in the Themes 'menu' (you'll see it there).

---

### Post by The Tronyx on 2006-09-26
> **bodhi.zazen said:**
> Copy your folder with your new theme to your ~/.enlightenment/themes folder. Then, start X11 and in enlightenment 'select' the new theme in the Themes 'menu' (you'll see it there).

I'm sorry, that went over my head.  Can you explain a bit more?

---

### Post by bodhi.zazen on 2006-09-26
> **2point0 said:**
> I'm sorry, that went over my head.  Can you explain a bit more?

sorry :redface:

Start at the beginning then:
First download your theme (nix-DR16.tar) To the desktop is OK

Open a terminal:
```
cd ~/Desktop
```
~ is short hand for /home/user_name

Now un-tar:```
tar -zxvf nix-DR16.tar
```
This creates a new directory nix-DR16 in/on your desktop.

dot file (.enlightenment for example) are "hidden". in the terminal you can see them with ```
ls -a
```
With nautilus check off the view hidden option in the pull down menu.

Lets move the file:```
mv ~/Desktop/nix-DR16 ~/.enlightenment/themes/
```

Now log out and log into Enlightenment. The theme should be available from the Enlightenment change theme menu.

---

### Post by The Tronyx on 2006-09-26
brooks@brooks-desktop:~/Desktop$ tar -zxvf nix-DR16.tar

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
brooks@brooks-desktop:~/Desktop$

and when I run that command with the tar.gz file, I get files all over my desktop.  I'm not trying to be difficult >.<

Note: What do you mean by > With nautilus check off the view hidden option in the pull down menu.


Sorry I think this was a bit misleading on my account, I don't have enlightenment installed yet, I was asking if there is a simpler way to install it becuase when I go through the ./configure routing and eventually install, I am told that I am missing a library file.  I won't lie, I have no firm basis as to what the hell I am doing, just reading books and googling until I go blind trying to learn as I go.  Thanks for your patience.

[http://enlightenment.sourceforge.net/Enlightenment/Get_Enlightenment/](http://enlightenment.sourceforge.net/Enlightenment/Get_Enlightenment/) also says I need other things in order to install and run enlightenment.  I don't know how to apply these things yet.  Honestly, if you told me to throw out cancel my ISP right now, I wouldn't blame you. ](*,)

---

### Post by bodhi.zazen on 2006-09-26
LOL :lol: sorry mate.

First install Enlightenment to use the theme. E16 is in the repositories.

For E17: [[color=blue]E17[/color]](http://ubuntuforums.org/showthread.php?t=20216)

Clean up your mess (desktop) !!!!!

Try right clicking and extracting the file (from the GUI) this time.

Nautilus is you file manager. On the top it has some pull down menus. Look under view and tag (select) the hidden or view hidden to see your hidden files.

---

### Post by The Tronyx on 2006-09-26
I'm feeling dumber by the minute...

I went to the synaptic package manager and searched for E16 and elightenment but came up with nothing.  Do I need to add a repository for E16?

---

### Post by bodhi.zazen on 2006-09-26
In a terminal:```
sudo gedit /etc/apt/source.list
```

Remove the # in front of the repositories.

Save and exit.

Re-start synaptic.

---

### Post by The Tronyx on 2006-09-27
Alright, I have enlightenment and I have the theme I want, in both .tar and .tar.gz formats.

I tried to pick up where we left off, but where should I go from here?

---

### Post by bodhi.zazen on 2006-09-27
At it again ??

Not sure of the nameo of your file .tar.gz .......

Start at the beginning then:

Open a terminal:
```
cd ~/Desktop
```

Now un-tar:```
tar -zxvf nix-DR16.tar.gz
```
This creates a new directory nix-DR16 in/on your desktop.

dot file (.enlightenment for example) are "hidden". in the terminal you can see them with ```
ls -a
```
With nautilus check off the view hidden option in the pull down menu.

Lets move the file:```
mv ~/Desktop/nix-DR16 ~/.enlightenment/themes/
```

Now log out and log into Enlightenment. The theme should be available from the Enlightenment change theme menu.

---

### Post by The Tronyx on 2006-09-27
Bodhi, at the end of this, I'm going to something really nice, like write your name on the moon. :mrgreen: 

tar -zxvf nix-DR16.tar.gz doesn't make a new folder on my desktop, it dumps files all over my desktop.

---

### Post by bodhi.zazen on 2006-09-27
:lol:

```
mkdir ~/.enlightenment/themes/nix
nautilus ~/.enlightenment/themes/nix
```
This should open your file browser (nautilus) to the directory:

~/.enlightenment/themes/nix

which should be empty.

Drag all those files from the desktop to that directory, logout, and restart enlightenment.

---

### Post by bodhi.zazen on 2006-09-27
How is your monitor? did those likns help?

---

### Post by The Tronyx on 2006-09-27
Oh man, I don't even want to get this thread started on my monitor.  I tried to manually change those values but my computer still tried to implode so I ran

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Since you asked though, I will tell you that I went to the wiki and the first main section didn't work, I am now trying  Method 2: Generating/Installing Ubuntu packages for the new 8.29.6 drivers in Ubuntu Dapper Manually.  I'll be sure to let you know how that goes for me. =]

I want to get this theme set up first.  I did what you said, and installed those files to the directory I made, but when I change to enlightenment, nothing comes up, well, something comes up, but its pretty vacant, and looks a bit superior to my knowledge still.

---

### Post by bodhi.zazen on 2006-09-27
If it looks gray and plain that is the default E16.

I do not recall where in the default menu the option is given to change themes. Find it and change themes before you head implodes ! :)

---

### Post by bodhi.zazen on 2006-09-27
Try this:

Click the middle mouse button
There should be a menu with an option for themes

Change it to nix.

---

### Post by The Tronyx on 2006-09-27
Haha?  Well the middle mouse button worked just fine, but my desktop looks nothing like the screenshot I saw =X  I guess I'm not up to that level of customization yet.

---

### Post by bodhi.zazen on 2006-09-27
> **2point0 said:**
> Haha?  Well the middle mouse button worked just fine, but my desktop looks nothing like the screenshot I saw =X  I guess I'm not up to that level of customization yet.

Screenshot is in order.

What does it look like?

---

### Post by appdx on 2006-10-15
I can't find e16 in the repos, can anyone help me out?

---

### Post by bodhi.zazen on 2006-10-15
> **appdx said:**
> I can't find e16 in the repos, can anyone help me out?

Look up....

See post #8 of this thread. 8-)

---

### Post by appdx on 2006-10-16
yes, I know but none of the repos has # in front of it in my sources.list

---

### Post by bodhi.zazen on 2006-10-16
So what happens when you {code]sudo aptitude update
sudo aptitude install enlightenment[/code]

This should install enlightenment, E16 is the version in the Ubuntu repostiories.

If you use synaptic, search "enlightenment".

---

