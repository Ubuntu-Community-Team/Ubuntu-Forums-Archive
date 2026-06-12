---
title: "Xubuntu &quot;root&quot; user question"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Tony Amidei on 2007-09-10
I just installed Xubuntu 7.04 got it working fine and istalled the RPM of Flash Player for Firefox.  Here are my questions:

1.  How do I unpack it correctly?  I think I did that correctly already but I cannot Run the Start-up file.
2.  How do I get it to run the install?  I think it is because I am not logged on as 'root' or 'admin' or something like that.
3.  How do I verify that it is working correctly with Firefox?

Thanks in advance.

---

### Post by kerry_s on 2007-09-10
> **Tony Amidei said:**
> I just installed Xubuntu 7.04 got it working fine and istalled the RPM of Flash Player for Firefox.  Here are my questions:

1.  How do I unpack it correctly?  I think I did that correctly already but I cannot Run the Start-up file.
2.  How do I get it to run the install?  I think it is because I am not logged on as 'root' or 'admin' or something like that.
3.  How do I verify that it is working correctly with Firefox?

Thanks in advance.

all *ubuntus are debain based. to install flash>
in terminal> sudo apt-get install flashplugin-nonfree
or use synaptic to install

make sure you turn on all your repos.

---

### Post by mcduck on 2007-09-10
1. You'd be better off using the flash player from Ubuntu's own repositories. [http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

2. There is no need for root in Ubuntu, the first user created is able to get temporary root privileges by using 'sudo' [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

3. Go to any site that uses Flash?

You may also want to read this one: [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

---

### Post by kerry_s on 2007-09-10
> **mcduck said:**
> 1. You'd be better off using the flash player from Ubuntu's own repositories. [http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

2. There is no need for root in Ubuntu, the first user created is able to get temporary root privileges by using 'sudo' [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

3. Go to any site that uses Flash?

You may also want to read this one: [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

way better than mine, man you make me feel lazy :lolflag:

---

### Post by Tony Amidei on 2007-09-12
Ok all of the comments and links are helping lots to get me more familar with Xubutu but I have two observations that seem to be stopping me from completing the task:
 
1. When i attempt to open Terminal (Applications -> Accessories -> Terminal) my computer the screen flashes what looks like the Terminal application and then it goes away and a login box pops up asking for first name then password.

2. Next after this did not work i attempted to drag and drop the libflashplayer.so file into the /use/lib/mozilla-firefox folder.  It would not work but i did notice that this folders 'permissions' is set to 'root'.

Could someone make some sense of this to me?

Over and Out.:(

---

