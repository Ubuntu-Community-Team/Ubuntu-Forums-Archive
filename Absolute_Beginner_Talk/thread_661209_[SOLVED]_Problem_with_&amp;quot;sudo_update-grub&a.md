---
title: "[SOLVED] Problem with &amp;quot;sudo update-grub&amp;quot; command on Fluxbuntu..."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Adbru on 2008-01-07
Hello Folks,

Another n00b with a question :redface:

I have installed Fluxbuntu 7.10 and have a problem which is answered on the Fluxbuntu forum, however, I cant get the command to do as its supposed to ?? 
Problem- Slow boot time and torn graphics once booted.
Solution - disable the splash screen on booting by editing the grub command and then typing "sudo update-grub".

If I edit the grub file then the system boots quickly (60secs for an old P3 500 laptop).
I then open a terminal window and run the command, it asks for a password (i enter my user password), it then appears to work - says its updating the "/boot/grub/menu.lst" file.

But when I reboot I have the splash screen problem back again.

I would be grateful for any help and thank you in advance.

Adbru

(I am still waiting for my account to be enabled  on the fluxbuntu forum hence why I'm asking here ....)

---

### Post by bodhi.zazen on 2008-01-07
Your account on Fluxbuntu is now activated :)

I think all you need to do is edit /boot/grub/menu.lst without running "sudo update-grub".

What I think you want to do is edit the options section :

> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=xxx-yyy-zzz ro

Note the last line "# kopt=root=UUID=xxx-yyy-zzz ro"

Edit the options you want on that line. Keep the leading #

In that section 

## Two hash marks = comments
# One hash mark = configuration options


HTH

---

### Post by xeth_delta on 2008-01-07
Can you please post your **/boot/grub/menu.lst**?

---

### Post by Adbru on 2008-01-07
Hi and thanks for the swift replies :)

Looking in boot.lst , in the default options "quiet" and "splash" are not shown but they are shown just after the default options section

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d12d6b51-7dea-43db-a363-a115e50e17ca ro

--------

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12d6b51-7dea-43db-a363-a115e50e17ca ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


Adbru

---

### Post by xeth_delta on 2008-01-07
If you comment out "quiet splash" the splash screen will not be shown anymore. You won't need to reconfigure grub.

From:
```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d12d6b51-7dea-43db-a363-a115e50e17ca ro quiet splash
```
To:
```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d12d6b51-7dea-43db-a363-a115e50e17ca ro #quiet splash
```

Xeth

[EDIT] Please read post #7 before making any changes.

---

### Post by bodhi.zazen on 2008-01-07
Sorry, I was a bit off :

> - So here's solution one:

For this open a terminal my right-click on the desktop and choosing 'Terminal'
Edit /boot/grub/menu.lst by starting an editor as superuser root:
 sudo gedit /boot/grub/menu.lst

Remove 'quiet' and 'splash' in the follwing part of menu.lst:
Note: depending on your setup there might be more options not only quiet and
      splash. Don't delete this other options, only delete quiet and splash.

  ## additional options to use with the default boot option, but not with the
  ## alternatives
  ## e.g. defoptions=vga=791 resume=/dev/hda5
  # defoptions=quiet splash

to:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

So by removing the defoption 'quiet splash' entry the splashscreen wil not be
used anymore

After you've done the changes you have to initialize the new grub bootloader
entry. Again in a terminal start:
 sudo update-grub

You will see that grup rewrites it's boot entry.
So we're done.
You may now close the Terminal and reboot the system to see the changes

[https://answers.launchpad.net/ubuntu/+question/7197](https://answers.launchpad.net/ubuntu/+question/7197)

---

### Post by bodhi.zazen on 2008-01-07
> **xeth_delta said:**
> If you comment out "quiet splash" the splash screen will not be shown anymore. You won't need to reconfigure grub.

From:
```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d12d6b51-7dea-43db-a363-a115e50e17ca ro quiet splash
```
To:
```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d12d6b51-7dea-43db-a363-a115e50e17ca ro #quiet splash
```

Xeth

Yea, they will change back when he updates grub (ie "sudo update-grub" or installs a new kernel) unless he changes the default grub configuration.

---

### Post by xeth_delta on 2008-01-07
> **bodhi.zazen said:**
> Yea, they will change back when he updates grub (ie "sudo update-grub" or installs a new kernel) unless he changes the default grub configuration.

Hmm, I did not know that, thanks for the observation. I guess one learns new things each day :)
I have always edited menu.lst / grub.conf manually, without using update-grub for custom kernels. From what you say should I understand gub-update is called whenever a new kernel is installed via the package system?

Xeth

---

### Post by Adbru on 2008-01-07
Many thanks for your help guys, Problem now sorted :)

I had some unix experience many many moons ago (anyone remember Ultrix !!) , having a ball playing with Linux (albeit very slowly and badly lol ).

Lots more reading on the forums to be done......and no doubt more questions as well :lolflag:

I was looking for a distro to run on this old laptop as XP was killing it, the ubuntu live cd took 10 mins to boot :( so I heard about fluxbuntu and here I am.

Adbru

---

### Post by xeth_delta on 2008-01-07
> **Adbru said:**
> Many thanks for your help guys, Problem now sorted :)

I had some unix experience many many moons ago (anyone remember Ultrix !!) , having a ball playing with Linux (albeit very slowly and badly lol ).

Lots more reading on the forums to be done......and no doubt more questions as well :lolflag:

I was looking for a distro to run on this old laptop as XP was killing it, the ubuntu live cd took 10 mins to boot :( so I heard about fluxbuntu and here I am.

Adbru

Great! Good luck and please write about your experience with Fluxbuntu!

Xeth

---

### Post by bodhi.zazen on 2008-01-07
> **xeth_delta said:**
> Hmm, I did not know that, thanks for the observation. I guess one learns new things each day :)
I have always edited menu.lst / grub.conf manually, without using update-grub for custom kernels. From what you say should I understand gub-update is called whenever a new kernel is installed via the package system?

Xeth

That is my understanding, although I am not a GRUB expert.

@Adbru : Fluxbuntu is a nice option, although you will learn the command line fast.

Alternates may include Zenwalk, Wolvix, or Mint (there is a Beta version with Fluxbox).

If all else fails, there is DSL, although that may be a little too light.

---

