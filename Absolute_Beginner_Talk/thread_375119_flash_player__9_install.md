---
title: "flash player  9 install"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by rdh on 2007-03-03
I'm trying to install flashplayer 9 . I have downloaded it to desktop, and unpacked it. In the installation instructions, it says...  Installation instructions
-------------------------

Installing the plugin tar.gz using Install script:
   o Unpack the tar.gz file
   o In terminal, navigate to the unpacked directory and enter:
          + $ ./flashplayer-installer
          + Click Enter key and follow prompts

I have clicked on the terminal, and at the prompt, i have typed /home/bob/desktop/flashplayer-installer

This does not then work. I am a total novice at Ubuntu, and am at the bottom of the mountain that i wish to climb. Can anyone advise me where i can read help text on the use of the terminal, and how i *navigate to the unpacked directory*?

Many thanks  Bob Holderness:)

---

### Post by aysiu on 2007-03-03
Try this:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by angryfirelord on 2007-03-03
Well, you have one of two options:

1) Navigating folders throught the terminal is done with the *cd* command. In your case, execute **cd /home/bob/desktop**. Now, run **sudo ./flashplayer-installer** (you need sudo, a.k.a root or administrator powers to run it).

2) Launch Synaptic & click on Setting-->Repositories. Check the ones that have the word "backports". Now, search for something called *flashplugin-nonfree*. Click apply & it will set it up for you.

---

### Post by picpak on 2007-03-03
Go to System  > Administration > Synaptic. Go to Settings > Repositories > Internet Updates. Check "Backported updates". Click Close, then click Reload.

Then, search for and install **flashplugin-nonfree**.

Easy as pie. No wait, even easier. Ever try flapper pie? If you don't cut it right, all the crust falls off the pie and you're left with no crust and a dish full of crumbs. This is easier.

---

### Post by rdh on 2007-03-04
Thanks - i managed to get the second method to work!

When i tried the first method, i typed:

cd /home  which took me to the home folder, but when i tried cd /bob, it said no such file or directory. Can you suggest a site which explains the terminal commands and how to use them?

Thank you very much  Bob Holderness

---

### Post by peebly on 2007-03-04
Hi

Download the Flash Player .tar.gz for Linux.

Right click and select extract here.

Open the folder, you will find 4 files.

Double click on Flashplayer-installer and click run in terminal.

Follow the on screen instructions.

That's how I do it anyway.

---

### Post by angryfirelord on 2007-03-04
> **rdh said:**
> Thanks - i managed to get the second method to work!

When i tried the first method, i typed:

cd /home  which took me to the home folder, but when i tried cd /bob, it said no such file or directory. Can you suggest a site which explains the terminal commands and how to use them?

Thank you very much  Bob Holderness

...because when you did cd /home, you are in the home directory, which is where bob lives. However, when you tried cd /bob, bob doesn't exist there.

See, when you cd into a drectory, you are put there. It doesn't take you back out.

To get to bob from /home, all you have to do is type cd bob because it's inplied that you are already in /home.

If you get a little confused, think of / as the C drive in windows.

---

### Post by aysiu on 2007-03-04
Put another way, the slash means the top-level directory.

```
cd /home
cd /bob
``` means that within the top-level directory, there are these subdirectories:
/bin
**/bob**
/boot
/etc
**/home**
/lib
...

```
cd /home
cd bob
``` however, assumes that within /home there is a subfolder called *bob*... in other words, /home/bob

/home
/home/bob

---

### Post by rdh on 2007-03-05
I've got it guys - it seems so simple! Thank you for taking the time... Bob

---

