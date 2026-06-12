---
title: "[SOLVED] Add/Remove and Synaptic don't work"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2008-01-05
**If you had no net connection when you installed or upgraded to Gutsy this could be for you.**

Ok - you've just installed or upgraded and have your new shiny Ubuntu 7.10 and the first thing you try to do is install something and you get an error - with a bit of luck you might find this thread if you've searched before you post a thread. 

You might have an error that tells you that  > cannot be installed on your computer type (i386) 

or

You've got a Synaptic error that says - 
> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

or if you've tried to use Add/Remove, you've got an error that says -

> The list of applications is not available : Click on reload to load it

All is not lost we hope.

Open a terminal, that's in Applications > Accessories > Terminal - and paste this command in 

```
cat /etc/apt/sources.list
```

If you've got a long list of writing that you don't understand, does it look similar to this, with many # all the way down 

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:

```

If it does, particularly if you have lines which say

> # Line commented out by installer because it failed to verify:

then it isn't as bad as it seems a the moment

Take a breath, get yourself a cup of your favourite beverage and sit down
 - we'll make a backup first - so you can get used to doing that  :) , so paste this command in, now if you've only used the terminal just now - it's going to want you're password - but it won't show you it while you type - keep going and then enter -  it's an invisible password

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak
```

Now we can edit the file - there are many editors you can use - nano is used in the terminal, but for the moment, until you're more aware of that, we can use a graphical text editor - I use Ubuntu as my OS so the command below relates to that, if you are using Kubuntu  - replace **gksudo gedit** with **kdesu kate**, if you're using Xubuntu replace **gksudo gedit** with [B]gksudo mousepad
[/B]
```
gksudo gedit /etc/apt/sources.list
```
you'll need you're password again here 

the file is now open ready for editing.
So that you can use external sources - you probably have a line for the cdrom - it looks like this

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

put a **#** at the beginning of the line, so it looks like and it will stop the cdrom being used 
> #deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

now for all the lines which look like this, we need to change them so that you can get software from the internet

> #deb http:
we need to do the opposite and remove the **#**, so they look like this
> deb [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) gutsy main restricted

Save your file and close the editor.

Now, once again, paste these commands in to terminal, one at a time and entering after each
```
sudo apt-get update
sudo apt-get upgrade
```

Once the terminal has finished and you are once again at your desktop prompt, try running Add/Remove or Synaptic again, if all is well - welcome to Ubuntu. I fthis hasn't helped then now is the time to post a thread.

---

