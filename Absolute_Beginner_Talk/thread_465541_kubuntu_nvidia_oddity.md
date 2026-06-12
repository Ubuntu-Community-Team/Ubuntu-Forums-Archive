---
title: "kubuntu nvidia oddity"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by eduardoeltortuga on 2007-06-05
Downloaded nvidia driver to desktop. Killed X.  I cd to my desktop and installed. During install, nvidia says it needs libc dev files.  Install these files and nvidia driver. Restart x. Works great. See NVIDIA logo. Works Great! Me so happy! Restart my puter and get error message and text screen. Me so sad, me want to cry:( 

Advice please

---

### Post by starcraft.man on 2007-06-05
Uh, ok, well. I'm not sure exactly what went wrong. Quick way to get you back to GUI (I assume your in console). So first log in with your username and password. Then type the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Then use tab and select ok or the default on every screen (especially if your not sure) until you get to the driver menu. Then pick "nv", you can then continue till the end. It will save and you can restart the computer with the command:

```
sudo reboot
```

I hope thats the right one, I usually just push the button on the top right corner :p.

Someone correct me on reboot if thats wrong......

---

### Post by eduardoeltortuga on 2007-06-05
thanks for the help, but no luck:( Guess i'll  just have to reinstall  Kubuntu, Google nvidia driver install help. It's hit and miss this way, but there is usually something thta works. This is WAY to hard!
                                        thanks though

---

