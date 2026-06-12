---
title: "Java Install..what to do?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Literatka on 2006-09-06
I cannot get Java to install. I guess I'm not understanding the 'directions'. It says to install on the root but I don't know how to get there nor what the password would be as I am the administrator and my name is the 'home' folder.
What should I do?

---

### Post by mssever on 2006-09-07
What method are you using to install Java?

To do something as root, you type "sudo" before the command. You enter your password if asked. Ubuntu is a little different this way than most other Linux distributions.

If you post specific questions, somebody can probably help you.

---

### Post by Literatka on 2006-09-07
Well here's what's happening, I was trying to do this but I don't think I am doing it right. 



	    Installation Instructions

	   
Printable VersionPrintable Version

Linux download and installation instruction for the Java Runtime Environment (JRE)


This article applies to:

    * Platform(s):
      Red Hat Linux, SUSE Linux, JDS
    * Browser(s):
      Netscape 6.2x, Netscape 7, Mozilla 1.4+
    * JRE version(s):
      1.5.0





Install

To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l



Make sure the installation file has executable permission

   6. Start the installation process.Type:
      ./jre-1_5_0-linux-i586.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0 directory. When the installation has completed, you will see the word Done.



The installation completes

   8. The JRE is installed in jre1.5.(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.5.0 directory. Verify that the jre1.5.0 sub-directory is listed under the current directory. Type:
      ls



Verify the installation filename

The installation is now complete. Skip to the Enable and Configure section.

---

### Post by jd65pl on 2006-09-07
If you are just starting out in linux you may find automatix useful in which case check this out

first
[http://ubuntuguide.org/wiki/Ubuntu#Installing_additional_software_.28Automatix.29]("http://ubuntuguide.org/wiki/Ubuntu#Installing_additional_software_.28Automatix.29")

Next
[URL="http://www.getautomatix.com/wiki/index.php?title=Installation"]
http://www.getautomatix.com/wiki/index.php?title=Installation[/URL]

You can also find automatix in the respositories

---

### Post by monktbd on 2006-09-07
try
[https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html](https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html)

much easier to do.

---

### Post by Sbarton on 2006-09-07
I had some luck doing it this way. in Terminal type:
sudo aptitude update (you will probably be asked for password, type it) then type sudo aptitude install sun-java5-bin. 
Hopefully that will get things moving. You will be asked to accept a couple of things along the way, do so and hopefully you will have it installed.BTW this is the page in the forum I used. look at the post by jagot(thanks jagot)
[http://www.ubuntuforums.org/showthread.php?t=252337&highlight=install+java](http://www.ubuntuforums.org/showthread.php?t=252337&highlight=install+java)
Regards

---

### Post by Literatka on 2006-09-07
Nevermind, found it. :)

---

### Post by mssever on 2006-09-07
> **Literatka said:**
> 
This article applies to:

    * Platform(s):
      Red Hat Linux, SUSE Linux, JDS
    * Browser(s):
      Netscape 6.2x, Netscape 7, Mozilla 1.4+
    * JRE version(s):
      1.5.0
I'm glad you've got it installed now. For future reference, though, I'd like to point something out: the instructions apply--it says--to Red Hat and SUSE, not Ubuntu or Debian. This is important because software installation is very different in Red Hat/Suse as opposed to Debian/Ubuntu. Until you gain enough experience with Linux, you should stick to instructions for Ubuntu (best) or Debian (second best).

This is assuming--of course--that you're using ([kx]|ed)?ubuntu. Of course, this *is* an Ubuntu forum...

---

