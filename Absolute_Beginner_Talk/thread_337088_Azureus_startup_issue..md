---
title: "Azureus startup issue."
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-01-12
Heyall

I installed Azuerus on my Edgy - box, and it works fine with my torrents. However, I need to "sudo azureus" to get it to run, and concequently all my downloads are owned by root when downloaded so that I have to "sudo nautilus" to move them or whatever. Now, this is a small problem as I know I can just change permissions, but I was just wondering if anyone knows a  way to avoid this issue, and downloading as normal user?

thx anyways!

---

### Post by Bachstelze on 2007-01-12
What happens when you try to run *azureus* without sudo ?

---

### Post by lodravah on 2007-01-12
it starts up, then shuts down as quickly again.. Won't run unless "sudo'd."

---

### Post by Bachstelze on 2007-01-12
No output in the terminal ?

---

### Post by lodravah on 2007-01-12
When I try to run from terminal - not sudo, then the same thing happens as when I run it from "Apps - Internet." It starts up then shuts down. I can't give you the terminal output right now as I'm currently downloading something, and when I tried to open "non - sudo" azureus it just said that I already have a version running.

---

### Post by lodravah on 2007-01-12
But it is almost done (61%) so I'll be able to give you terminal output in a little while!

---

### Post by hardyn on 2007-01-12
read around, the repository version is broken.

you have to download the new .jar for azureus, and copy it into the azureus directory; all will be well after that.

---

### Post by lodravah on 2007-01-12
Mokay, I'll read around a bit. What is the *.jar - file?

EDIT: Ah, java - file. I see..

---

### Post by lodravah on 2007-01-12
This is the output from trying to run "azureus" - non root in terminal:

changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb05bfd02, pid=16876, tid=3085289136
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid16876.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by AstarothCY on 2007-01-27
To clarify for anyone who still has this problem, you need to download the latest azureus tar.bz2 from the azureus homepage, extract it into a directory and read the Readme file for further instructions.

---

### Post by rururudy on 2007-02-25
Here are the exact steps I did to fix the problem on my desktop:
 [LIST=1]
[*]Download new azureus
[http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php")
[*]switch to root
*sudo su*
[*]remove old azureus
*rm -rf /usr/share/azureus/*
[*]unpack new azureus 
*bunzip2 -c Desktop/Azureus_2.5.0.4_linux.tar.bz2 | ( cd /usr/share ; tar -xvf - )*
[*]update azureus script
[I]cat /usr/share/azureus/azureus > /usr/bin/azureus
chmod 755 /usr/bin/azureus[/I]
[*]edit the azureus startup script
*gedit /usr/bin/azureus*
The forth line should read like this:
 **PROGRAM_DIR="/usr/share/azureus"**
[*] You are done!  exit your sudo session (type exit) and then type the command 'azureus'
[/LIST]

:KS

---

### Post by kittyhawk63 on 2007-02-25
I followed your instructions and here is Terminal's reply:

kittyhawk63@kittyhawk63:~$ sudo su
Password:
root@kittyhawk63:/home/kittyhawk63# rm -rf /usr/share/azureus/
root@kittyhawk63:/home/kittyhawk63# bunzip2 -c ~/Desktop/Azureus_2.5.0.4_linux.tar.bz2 | ( cd /usr/share ; tar -xvf - )
bunzip2: Can't open input file /root/Desktop/Azureus_2.5.0.4_linux.tar.bz2: No such file or directory.
root@kittyhawk63:/home/kittyhawk63#

I have the **Azureus_2.5.0.4_linux.tar.bz2 **file on my desktop.

What happened?

---

### Post by rururudy on 2007-02-26
Replace the tilda **~** with /home/YOURACCOUNT.
That ought to work...  or try this from your home directory (in your case **/home/kittyhawk63**:
[I]bunzip2 -c Desktop/Azureus_2.5.0.4_linux.tar.bz2 | ( cd /usr/share ; tar -xvf - )
[/I]

FYI,
**[COLOR="Red"]~[/COLOR]** is a shortcut in unix for your home directory, but it is trying to go to root's home directory.  My saved file was in /home/**rudy**/Desktop

---

### Post by kittyhawk63 on 2007-02-26
> **rururudy said:**
> Replace the tilda **~** with /home/YOURACCOUNT.
That ought to work...

(~ is a shortcut in unix for your home directory, but it is trying to go to root's home directory.  My saved file was in /home/**rudy**/Desktop, or somewhere like that...)

Terminal does not recognize that I have "HOME". 

Do I set up a HOME directory?

---

### Post by kittyhawk63 on 2007-02-26
RURURudy,
I'm a noobie and may not fully understand. However, I will try to do what you are telling me. I will remove the ~ and so on and then reinsert the command line and see what happens. How do I know what my account name is? Is it kittyhawk63@kittyhawk63~$  without the "~$" ?

---

### Post by benighted on 2007-02-27
your user's home directory will be: /home/your_user_name/

usually, this can be abbreviated simply with a ' ~ ', however, when you use terminal as root, you change the user running terminal to be root (though you are really the one using it), and root's home directory is simply /root/ 

This is why you're having problems with it telling you the file doesn't exist. 

when you're running terminal as root, remember to use the full address for files in your own user's folder, not just ~ (which will go to root's home folder -- because you're running terminal as root, remember?) 

it might go round in circles a bit, but I think it should be understandable :p

---

### Post by kittyhawk63 on 2007-02-27
> **benighted said:**
> your user's home directory will be: /home/your_user_name/

Thanks, I will give it a go.
Kh

---

### Post by _ziggy_ on 2007-03-10
Instead of installing Azureus from source try this:

```
rm ~/.azureus/logs/debug_1.log
```

My Azureus has crashed immediately after the main interface screen loaded on two separate occasions.  Both times it happened in  6.10.  The first time was right after an upgrade from Dapper to Edgy; the second was when I was prompted with the Azureus donation reminder.  I have been able to recover each time by removing the debug log file as illustrated above.

---

