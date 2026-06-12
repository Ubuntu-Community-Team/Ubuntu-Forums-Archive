---
title: "NVIDIA driver - X server cannot be killed"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by John Boy on 2007-06-24
Have downloaded NVIDIA-Linux-x86-100.14.11-pkg1.run and when I try to follow the install instructions it detects that I have an X server running (likely KDE). the log mentions the PId so I kill it but it comes back. In other places I have seen being told to edit inittab but I cannot find that file. I believe that if I set the runlevel to 3 I wil be OK but without inittab on my Kubuntu installation, I am stuck.

          Thanks for any help,

                                          Slainte,

                                                     John

---

### Post by Titus A Duxass on 2007-06-24
Do Ctrl+Alt+F1 and get into another terminal,
login as normal user,
then "sudo /etc/init.d/gdm stop" (or kdm).

Alternatively install nvidia drivers with Automatix or through aptitude as follows:

sudo aptitude install nvidia-glx
sudo nvidia-xconfig

Aptitude should bring down all the required packages (kernel images, etc.), you will have to restartx.

Any problems after just run "sudo dpkg-reconfigure xserver-xorg", don't forget to select nvidia during the process.

---

### Post by John Boy on 2007-06-25
Thanks - that worked like a charm (the killing X server anyway). Nvidia installer seemed to do it's thing but am getting the same problem as reported recently by keyboardman (black screen, flashing white cursor) and had to go back to old version of xorg.conf because installer changed

          Identifier "Generic Video Card"
          Driver "vesa"
          BusID  "PCI:0:13:0"

          to Driver "nvidia" and deleted the BusID line

I have GeForce 6100/nForce but will wait to see what advice keyboardman gets.
 
      Slainte,

---

