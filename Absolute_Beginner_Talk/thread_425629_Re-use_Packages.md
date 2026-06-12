---
title: "Re-use Packages"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by staf4t5 on 2007-04-27
is it possible to re-use packages downloaded from the repos if you need to do a re-install.

---

### Post by Martin on 2007-04-28
Yes, take a look in /var/cache/apt/archives and you should see a whole lot of your recent updates. Copy these somewhere else or burn them onto a dvd or .... Once you have reinstalled put the files back into /var/cache/apt/archives. Run synaptic or apt-get or whatever software you use and the system will make use of them. I'm sure there are more elegant ways but this works for me.

---

### Post by staf4t5 on 2007-05-25
It does not allow me to copy to the folder "/var/cache/apt/archives" so i cant install the packages...:(

---

### Post by quinnten83 on 2007-05-25
try with the sudo command?

---

### Post by nhandler on 2007-05-25
sudo will only help you if you are performing the copy using the terminal. If you wish to perform the copy graphically (using nautilus), use this command 'gksudo nautilus'. That will prompt you for you password. After that, it will launch a file browser. This is a file browser run as root, so it can copy files to any folder. After you copy your files, be sure to close this file browser to prevent accidentally messing up your system.

---

### Post by mcduck on 2007-05-25
you can also just open the directory where you have alll those files in a termional and run 'sudo dpkg -i *.deb' to install them all ;)

---

### Post by staf4t5 on 2007-05-25
WOW thanks everyone esp mcduck...the sudo dpkg -i *.deb was so easy to use and it was done in seconds....:biggrin:

---

