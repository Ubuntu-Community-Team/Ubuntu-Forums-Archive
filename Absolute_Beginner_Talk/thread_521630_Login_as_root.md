---
title: "Login as root?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Terje1972 on 2007-08-09
I'm very new with Ubuntu and Linux.

And now I feel stupid.
How do I login as root?  I tried to login with "root" in the login-screen with password, but that didn't work.

The thing is that I am installing Win4Lin, and need to login as root to run a command in the terminal.

Anyone please?

Terje

---

### Post by oilchangeguy on 2007-08-09
in the terminal type sudo before your command.

---

### Post by raja on 2007-08-09
preface your command with sudo and the command will be executed with superuser status (after you give your password). Using sudo is safer than logging in as root (which you do with 'su').

---

### Post by bodhi.zazen on 2007-08-09
Or, if you want to log in as root. use : 

```
sudo -i
```

---

### Post by stchman on 2007-08-09
> **Terje1972 said:**
> I'm very new with Ubuntu and Linux.

And now I feel stupid.
How do I login as root?  I tried to login with "root" in the login-screen with password, but that didn't work.

The thing is that I am installing Win4Lin, and need to login as root to run a command in the terminal.

Anyone please?

Terje

There is no root account that you can access.  If you want to do tasks as root put a sudo in front of the command in the terminal.  This is how Linux is secure.  No running as root, no surfing internet as root, etc.

---

### Post by aysiu on 2007-08-09
Here are the instructions, according to [the Win4Lin website](http://www.win4lin.com/index.php/content/view/120/153/): > How to install Win4Lin Pro.

   1. Obtain a license code.

      To install Win4Lin Pro download version, you must first obtain a valid license code. If you do not already have one, license codes may be purchased from our online store.

   2. Download the package.

      You can download the Win4Lin Pro packages from the Support->Downloads then choose Installers to pick the correct installer for your distribution.  menu. Download the Win4Lin Pro package in either RPM or .deb format. **For Debian GNU/Linux, Xandros, Linspire, download the .deb package.** For RedHat, Fedora Core, SUSE,  Novell, Mandrake, and most others, download the RPM package. If you are not sure what the preferred packaging format is for your Linux distribution, please consult your distribution's documentation. Record the name of the directory into which you download the package, as you will need it during installation.

      Go to Support -> Downloads -> Installers through the top menu.

   1. Read the documentation.

      Read the Users Guide for installation instructions and consult the product Release Notes for the most up-to-date information. Current documentation including Users Guide and the Release Notes are located under Support -> Documents. If you obtained a license, download the .deb package and double-click it. If you didn't obtain a license, I'm closing this thread.

---

### Post by Terje1972 on 2007-08-09
Thank you everyone.  So far so good!

(But I probably will cry out for help some time later)

Terje

---

