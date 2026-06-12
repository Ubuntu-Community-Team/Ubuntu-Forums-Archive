---
title: "Nvidia Drivers on Kubuntu problems"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by keyboardMan on 2007-06-24
H,i I am new to these forums and new to Linux:)

I have installed Kubuntu 64Bit as dual boot with Windows XP. I am running a AMD 4400X2, 2GB of Ram and a 7800GT Nvidia card. Well heres my problem...

I have found some information on the internet about installing Nvidia on Kubuntu this is what I did:

Opened adept>Typed Nvidia in the search field > Choose nvidia-glx > Clicked Install package > Applied the changes >opened Konsole > typed sudo nvidia-glx-config enable > Typed password > message stated that a restart would be required.

On restart I went in as usually only to be presented with a black screen and flashing white line in the left hand corner:-? :(

I hope someone here could help me please and bear in mind I am a beginner, so try not to confuse me:)

Thankyou
Regards
KeyboardMan

---

### Post by keyboardMan on 2007-06-24
bump

---

### Post by Butthead on 2007-06-24
Hmm, I don't know if this will help, but boot up in recovery mode (usually the second choice in the Grub menu), cd over to your /etc/X11/ directory, and then type in:

sudo dpkg-reconfigure -phigh xserver-org

Hopefully, when you reboot, it will bring up X windows in a low resolution.

Then, go get the Envy program, and follow the installation instructions for it explicitly.

Two things I have found is *don't* use the textual menu in Envy to install your NVIDIA driver, and restart (or reboot) X windows first to run Envy using it's GUI (Graphical User Interface).

---

