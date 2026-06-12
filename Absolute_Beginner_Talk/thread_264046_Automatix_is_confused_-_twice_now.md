---
title: "Automatix is confused - twice now"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-24
I running a Dapper install less than 60 minutes old. Aptitude and Synaptic both report nothing to update/upgrade.

Installed Automatix before ANYTHING else.

Installed Automatix using:

wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer

no errors or problems reported at the end of the install.

Re-booted. Dialed-up, ran Automatix, asked it to install Sun Java 1.5 JRE. Entered a password in the 'grey' box, then had to enter the password again in a separate box, but Arnie's worth it, what the heck!

Suprise! Suprise! Automatix reported Java as INSTALLED. I surfed over to Java.com and ran the install verification.

JAVA is simply NOT installed on this computer. It isn't possible. And this is the second time that Automatix claims to have installed or claims to have found installed a program that it isn't possible for it to have installed or have found or located on the disk/system.

What gives?

PS -- I'm running Swiftfox on a stock Dell 4100 box.

---

### Post by siacs on 2006-09-24
You may still need to specify which Java version to use.

sudo update-alternatives --config java


As far as Automatix goes, [this is a better way]("http://ubuntuguide.org/wiki/Dapper") in my opinion.

---

### Post by Mark_in_Hollywood on 2006-09-24
OK, but how does this help? I ran the command and see two "types". AutoM is saying I HAVE: "Sun Java JRE 1.5" installed. It isn't installed.

---

### Post by siacs on 2006-09-24
That's why I gave you the link. If Automatix isn't doing the business just [do it manually]("http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox"). It's not hard, you can just copy and paste.

---

### Post by arnieboy on 2006-09-24
> **Mark_in_Hollywood said:**
> I running a Dapper install less than 60 minutes old. Aptitude and Synaptic both report nothing to update/upgrade.

Installed Automatix before ANYTHING else.

Installed Automatix using:

wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer

no errors or problems reported at the end of the install.

Re-booted. Dialed-up, ran Automatix, asked it to install Sun Java 1.5 JRE. Entered a password in the 'grey' box, then had to enter the password again in a separate box, but Arnie's worth it, what the heck!

Suprise! Suprise! Automatix reported Java as INSTALLED. I surfed over to Java.com and ran the install verification.

JAVA is simply NOT installed on this computer. It isn't possible. And this is the second time that Automatix claims to have installed or claims to have found installed a program that it isn't possible for it to have installed or have found or located on the disk/system.

What gives?

PS -- I'm running Swiftfox on a stock Dell 4100 box.

java probably is already installed (which is why AX is reporting it) but a few hours back, a bug was found which was preventing the java plugin to show up in swiftfox.
a bugfix update for AX has been released.
Just install "swiftfox" and swiftfox plugins" from the updated AX.
Remember: Installing Java will not install the java plugin for swiftfox (it will install it for firefox though). Swiftfox is a non standard install in a non standard location.

---

