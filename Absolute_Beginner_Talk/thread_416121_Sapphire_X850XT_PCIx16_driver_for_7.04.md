---
title: "Sapphire X850XT PCIx16 driver for 7.04"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-04-20
Hey, I just installed Ubuntu 7.04 on a computer that has a Sapphire ATI Radeon X850XT PCI Express x16 video card.  It has never been compatible with any other version of Ubuntu until this one.  It is great, but... I can only go to a resolution of 1024x768 with a refresh rate of 60 Hz.  With Windows XP, I can go to 1600x1200 with a refresh rate of 85 Hz.
Any way to do this with Ubuntu?

I'm very new,
Thanks

---

### Post by overdrank on 2007-04-20
> **mdknaebel said:**
> Hey, I just installed Ubuntu 7.04 on a computer that has a Sapphire ATI Radeon X850XT PCI Express x16 video card.  It has never been compatible with any other version of Ubuntu until this one.  It is great, but... I can only go to a resolution of 1024x768 with a refresh rate of 60 Hz.  With Windows XP, I can go to 1600x1200 with a refresh rate of 85 Hz.
Any way to do this with Ubuntu?

I'm very new,
Thanks

Hi and maybe this link will help with the graphics driver
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Good luck!:guitar:

---

### Post by mdknaebel on 2007-04-20
hmm, well after doing everything and getting to the text menu in terminal, i get an error that says 'rm: cannot remove `*.deb': No such file or directory
Your Operative System does not seem to be supported by Envy'

any ideas?

Thanks

---

### Post by overdrank on 2007-04-21
> **mdknaebel said:**
> hmm, well after doing everything and getting to the text menu in terminal, i get an error that says 'rm: cannot remove `*.deb': No such file or directory
Your Operative System does not seem to be supported by Envy'

any ideas?

Thanks

Hi I was afraid of that, once I saw that you were using Feisty. Sorry I have no idea but maybe someone else will chime in. :(

---

### Post by aberry5555 on 2007-04-21
you will need to edit your xorg.conf file in order to do it. You can either do it manually (open the file in a text editor and scroll down till you see resolutions) or by trying this command:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

then restart your computer. Once it's restarted go in to the settings and see if you can change the resolution.

---

