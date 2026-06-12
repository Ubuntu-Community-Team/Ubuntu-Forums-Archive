---
title: "Error message"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by quasismart on 2007-01-05
I continue to get an error meesage when I boot up in Ubuntu. It says:
"Could not lok up internet address for .
 This will prevent GNOME from operating correctly.
 It may be possible to correct the problem by adding
  to the file /etc/hosts."

  Then I have the option to Login Anyway or Try Again. After I log in anyway and go to the terminal, I can not access any files. I get this message:
"unable to look up  via gethostbyname()"

I think that the computer name has been changed?? Does anyone have any ideas??

Quasismart says smart people can do dumb things to!!

---

### Post by kingmonkey on 2007-01-05
Is this why your where going to reinstall?

Boot up into recovery mode or boot into terminal and edit the /etc/hosts file by typing:

```
 sudo nano /etc/hosts 
```

Make sure the lines:
127.0.0.1 localhost
127.0.1.1 yourcomputername

is there or it wont work. Delete everything else for now. Save it. Reboot. Hopefully it will work.

---

### Post by quasismart on 2007-01-05
I will try this and repost in a few.
Thank you.

---

### Post by quasismart on 2007-01-05
When the recovery mode boot stops I am at :
"root@:~#"
I tried sudo nano /etc/hosts and got the same  gethostbyname message.

---

### Post by quasismart on 2007-01-05
Sorry for the mess. I typed in the line without the sudo and this is what came up:

127.0.0.1 localhost.localdomain  localhost

#The following lines are desireable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Thats all.

---

### Post by kingmonkey on 2007-01-05
In my /etc/hosts

I have an extra line which is:

127.0.1.1 mycomputername

Add this line to your substituting mycomputername for your computer name.

---

### Post by kingmonkey on 2007-01-05
Also edit your /etc/hostname file so that it has the correct hostname

---

### Post by quasismart on 2007-01-05
I changed it out as you said and removed the rest of the file. I still get the error message about GNOME, But i do not have any ability to use sudo command in terminal. I checked the /etc/hosts file and it is just the way you said. Is the "mycomputername" saved somewhere already or can I use anything that I want?

---

### Post by kingmonkey on 2007-01-05
mycomputer name should be same as the one in /etc/hostname

anyway I found this thread which seems to describe the exact same problem:

[http://www.ubuntuforums.org/showthread.php?t=188337](http://www.ubuntuforums.org/showthread.php?t=188337)

---

### Post by quasismart on 2007-01-05
I typed in nano /etc/hostname and it was empty. Can you tell me what it should look like?
Thank you for the help so far.

---

### Post by kingmonkey on 2007-01-05
you need to make sure that your computername is the same in /etc/hosts and /etc/hostname

So /etc/hostname should look like this:

```

yourcomputername

```

and /etc/hosts should look like:

```

127.0.0.1       localhost yourcomputername

```

Be sure to reboot afterwards.

---

### Post by quasismart on 2007-01-05
Let me say thank you very much for the help. I am finally back to normal and can get away from that other OS. Thank you again for all of the help. I have been trying to fix this on my own for about 3 months, then I came across this website today. Have a good one.

---

