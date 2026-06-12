---
title: "Eee pc"
date: 2011-08-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mattig89ch on 2011-08-01
hi all, i have an asus EEE PC netbook and have grown rather tired of windows (more specifically the malware i can't seem to remove no matter what i do).

anywho i put a live disk onto my flash drive using unetbootin, booted into it, and was delighted to find out that the driver for my wireless card were there.  upon trying to install the os, i keep getting errors.  restarting for the first time the machine shuts down it ways that some of the sectors on the hard drive are having trouble.  when i boot back up it says "there is a problem with the configuration server.  (/usr/lib/libgconf2-4/conf-sanity-check-2 exited with status 256)"

the live disk runs with no problems, but it seems something goes wrong with the install.  is there anything i can do to fix this?

btw, there is no disc drive, and my external disc drive isn't recognized as a boot device.

---

### Post by sanderd17 on 2011-08-01
If you see the first purple screen, can you hit a key?

Normally hitting a key should take you to a text based menu, and I believe you're able to preform a fsck (file system check) from it. Do that and see if you hdd has some bad sectors.

If you have 11.04, it's far from a good release. Some Linux users called it "the Vista of Ubuntu". So maybe you could try the 10.04 LTS or the 10.10 release. I like the 10.10 release more, but it will only be supported until April 2012 (so after that, you won't get new updates). The 10.04 LTS (long term support) will be supported until April 2013.

You can Download 10.10 here: [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/), for 10.04, you can use the normal download page.

---

### Post by mattig89ch on 2011-08-01
first purple screen?  I don't see a purple screen.


when the os selection menu comes up i select ubuntu, with linux 2.6.32-33-generic-pae

and it takes me to the loading screen with 5 dots.  then it throws the error message and gives me a log in.

could the fact that I'm not erasing windows be the issue?


Edit: spelling errors

---

### Post by sanderd17 on 2011-08-01
Sorry, the first purple screen of the live disk, not of the installation. I should have been more clear.

You can also run the command 
```

fsck

```
from a live disk if you don't find that menu.

---

### Post by mattig89ch on 2011-08-01
just out of curiosoty, the 'check disk for defects' option when booting from the flash drive is the same thing as fsk correct?

edit: oh and i couldn't seem to get to the command prompt w/out getting onto the desktop of the live disk.  when I type in 'fsck' it says 'fsck from util-linux-ng 2.17.2'

---

### Post by sanderd17 on 2011-08-01
yep

---

### Post by mattig89ch on 2011-08-01
i'm asuming that yep was to the first part.  if so, then it says there are no errors on the hard disk.

here's a question, if i tell it to install over the entire hard drive (xp included) will it import the files from xp before formatting them?

---

### Post by snowpine on 2011-08-01
> **mattig89ch said:**
> i'm asuming that yep was to the first part.  if so, then it says there are no errors on the hard disk.

here's a question, if i tell it to install over the entire hard drive (xp included) will it import the files from xp before formatting them?

No it will not. You need to BACK UP anything from Windows that you want to keep!

But you shouldn't be installing yet. You should be trying Ubuntu in "Live" mode with no change to your computer. If you can't get it working in Live mode then don't blow away your Windows install with something that might not work!

---

### Post by sanderd17 on 2011-08-01
> **mattig89ch said:**
> i'm asuming that yep was to the first part.  if so, then it says there are no errors on the hard disk.


It's good that there are no errors, but weird.
> 

here's a question, if i tell it to install over the entire hard drive (xp included) will it import the files from xp before formatting them?

Are you ready to lose Windows? A lot of users still need Windows for some little thing. I don't need it anymore, but I also strugeled for about a year.

About your documents, no, it won't save them. Since formatting the HDD will do that to the whole HDD at once, you don't have enough memory to store those files.

What I would do is the following:

[LIST]
[*]Defragment the windows partition
[*]Shrink the Windows partitions to about 120% of the space they really need. You can do that with a windows partitioner or with the gParted program on the live USB.
[*] create a new partition with gParted, format it as ext4 and copy all your files to it. This will be your home directory. (Don't forget to apply the changes with the green V-sign)
[*] If you are sure you saved all your files, delete the windows partitions
[*] start the install wizard. When you are asked where it should be installed, choose manual mode.
[*] In the manual mode, pick the unformatted (the former windows space) as root, format it as ext4. And pick the partition you created before as home.
[*] finish the installation and boot the new OS. You files should be in your home directory.
[/LIST]

This is how it should work. But you have to make a backup. If you select something wrong in the installer or in gParted, you can erase everything on your computer (yes, I have done this before :oops:). Or if the computer would crash (for any reason) you can also lose all your data.

EDIT: +1 for trying in Live mode first.

---

### Post by mattig89ch on 2011-08-01
thanks for all the help so far guys.  guess i'm backing up the files.

I don't really do much more then surf the web and listen to music on this machine.  and windows is giving me hell with the keyboard.

the live disc recognizes my wireless nic, sound card, and has no trouble with the keyboard.  as far as i'm concerned ubuntu gives me everything i need with this machine.  while it will suck that i can't really play diablo or freelancer, its a small price to pay to get this machine back to operation status.

i will say this, if i could get my current install of ubuntu working then i won't need to wipe windows and can have the best of both worlds.  so before i blow away windows (to use your words) what else can i do to get this up and running?

---

### Post by snowpine on 2011-08-01
Apologies, I misread your post that you had already installed Ubuntu.

I found a thread about this same issue, perhaps the solution here will help you?

[http://ubuntuforums.org/showthread.php?t=1467504](http://ubuntuforums.org/showthread.php?t=1467504)

---

### Post by mattig89ch on 2011-08-01
hm...well i haven't run any updates, however the error message apears the same.

after installing, it gave me the first error messages that there was something wrong with the hard disk (i think i've ruled out the hard disk being bad), then it just sat there with the errors (in command promt form, w/out giving me a command prompt), so i held the power button to shut it down.  and i get this error that we share in common.

could the improper shut down the the cause of this?


also, i don't know if this is related to the current issue or now, but after my last post i used the live disc to browse over to youtube.  after installing flash it said that the multi-universe portion of flash couldn't install.  when i tried to manually install it off adobe's web site, i would get to the point where i would dl and nothing happens.  when i tried to browse over to youtube again, it asked me to install flash player, i went through the steps to install it automatically it said that it couldn't find the package to install adobe flash.

could these two issues be related?  after all, i am using the same image to install the os.

---

### Post by snowpine on 2011-08-01
According to [http://ubuntuforums.org/showthread.php?t=1467504](http://ubuntuforums.org/showthread.php?t=1467504) the error is caused by an improper shutdown (such as holding down the power button). Have you tried the proposed solution?

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo poweroff
```

---

### Post by mattig89ch on 2011-08-03
well thats just it, i can't get to a console in anything but the live disc.

---

### Post by sanderd17 on 2011-08-03
Weird. Try CTRL+ALT+F1, then you will get in a real console. I believe it is CTRL+ALT+F7 in Ubuntu to return to the graphical environment.

---

### Post by mattig89ch on 2011-08-04
ok, i guess i've not been clear (or am not understanding).

I get to put in my password, it throws the error message, then the password message pops up again.  at no point am i put into a position to enter the cosole mode.

mind you, i'm not stranger to linux, but every time i ever used it, it was on a desktop pc and i never had any trouble getting to the desktop.  it was after i got to the desktop that i had any problems.

---

### Post by pifactory3142 on 2011-08-05
Have you tried xubuntu? 

See: [http://ubuntuforums.org/showthread.php?t=1801527](http://ubuntuforums.org/showthread.php?t=1801527)

I'm now running two old Aus eeepc machines on xubuntu with few issues.

---

### Post by mattig89ch on 2011-08-06
well....no i haven't.  um....what are these few issues you speak of?

---

