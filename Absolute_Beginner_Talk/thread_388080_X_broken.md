---
title: "X broken"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by laforge on 2007-03-19
Ok, so I was following [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29") guide to install Beryl.  It went well up to the configuring of X.  I did the backup and the edit, and after the ctrl+alt+backspace everything went wrong.

The screen went black for a bit and came up with an X server error or something of that sort.  If I try to load it up normally I get an error that says X is broken with a log and then after is just a black screen.  I can type but its not like I am in terminal or something.

Then I tried going into recover mode and doing the opposite of the backup
```
sudo cp /etc/X11/xorg.conf_backup /ect/X11/xorg.conf
``` then restart.  I still got the same error.  Is it not able to copy files over in recovery mode?

If there is a way to fix this without reinstall that would be great, but a reinstall wouldn't be that bad since there wasn't much on it.

Thanks for any help in advance.

---

### Post by kvonb on 2007-03-19
Make sure you got the spelling correct in that line, "etc" is wrong.

What video card do you have?

You can find out by typing:

```
lspci | grep VGA
```

To recover, once the computer boots to the black screen, press <CTRL><ALT><F1> to go to a "virtual terminal", you can login with your normal account.

A quick recovery is to type:

```
sudo dpkg-reconfigure xserver-xorg

```
...and choose "vesa" as the driver, that is a generic that will work.

Once you have got back to your desktop AND you have either an Nvidia or ATI card, go here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and follow his instructions.

Once the driver is properly installed, you can then continue onto Beryl.

Regards, KEv :)

---

### Post by laforge on 2007-03-19
Thanks very much for the quick response.  I will have to try that tomorrow.

Also i might of spelt something wrong.  It is a bit late.

Thanks again.

---

