---
title: "Quit typing the sudo command all the time"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by steve101101 on 2007-03-01
How to use "sudo" without prompt for password ***WARNING NOT SECURE***

code:

gedit sudo visudo

Find this line 

system_username	ALL=(ALL) ALL

Replace with the following line 

system_username	ALL=(ALL) NOPASSWD: ALL

Save

other beginner information can be found here [http://http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://http://ubuntuguide.org/wiki/Ubuntu_Edgy")

---

### Post by taurus on 2007-03-01
Sudo is there for a reason so I am not sure what's the purpose of this thread really is.

---

### Post by newlinux on 2007-03-01
sudo -i is perfectly sufficient. just typing the password once if what you really want is to not have to type sudo all the time.

---

### Post by steve101101 on 2007-03-02
one of my friends keeps getting tired to typing sudo and he is the sole user of the system.

---

### Post by taurus on 2007-03-02
> **steve101101 said:**
> one of my friends keeps getting tired to typing sudo and he is the sole user of the system.

If your friend keeps typing sudo, then I would consider asking why because there is no reason he needs to keep using sudo all the time.

---

### Post by steve101101 on 2007-03-02
I know, but the sudo command can get repetitive to type especially if your do many commands in the terminal and he has no risk of corrupting his system because he is the sole user. I know that the sudo command adds some security to prevent accidental mistakes from corrupting files so for me it make me double check what i have typed before i press <enter>.

---

### Post by slayerboy on 2007-03-02
> **steve101101 said:**
> I know, but the sudo command can get repetitive to type especially if your do many commands in the terminal and he has no risk of corrupting his system because he is the sole user. I know that the sudo command adds some security to prevent accidental mistakes from corrupting files so for me it make me double check what i have typed before i press <enter>.
If he goes online at all, he runs a real risk of getting his system fubar'd...seriously, that's why Linux is more secure because you HAVE to do this.  If he's running this way, he's no better off than using windows.

---

### Post by steve101101 on 2007-03-02
I also thought of this which is why i posted ***WARNING*** at the beginning on the thread.  I also like linux because of all the built in security.

---

### Post by 23meg on 2007-03-02
[QUOTE=steve101101]the sudo command can get repetitive to type especially if your do many commands in the terminal[/QUOTE]

Suggest your friend to use "sudo -i" if that's the main problem.

---

### Post by steve101101 on 2007-03-02
I know this is off topic, but since it seems like everyone is looking at this thread. My enlightment session is nolonger working. I am unsure why this happened. I was using e17, switched to gnome and then tried to switch back to e17. When I did this as soon as i loged in. It came up with a message that said...

Your session lasted less than 10 seconds ...

Please help.

---

### Post by steve101101 on 2007-03-02
i will give my friend all of the advice that all of you have offered. Thanks

---

### Post by Bagboy23 on 2007-03-02
There is no need to have a go at the guy. It's just useful information for the right people. I'll be using that trick when I experiment with my VMware version of Ubuntu.

---

### Post by steve101101 on 2007-03-02
I use ubuntu in vmware player on a windows XP pro desktop. if you have any questons just send me a message.

---

### Post by Bagboy23 on 2007-03-02
> **steve101101 said:**
> I use ubuntu in vmware player on a windows XP pro desktop. if you have any questons just send me a message.

Alright, you've put yourself out there and now you have to help when I need it :P 

:guitar:

---

### Post by steve101101 on 2007-03-02
will do. its the only way open source software and OS succeed is through user support and user forums. :-)

---

### Post by steve101101 on 2007-03-02
> **Bagboy23 said:**
> Alright, you've put yourself out there and now you have to help when I need it :P 

:guitar:

For good information you can also look to this site...
[http://www.petri.co.il/virtual_installing_ubuntu_as_virtual_machine.htm]("http://www.petri.co.il/virtual_installing_ubuntu_as_virtual_machine.htm")

---

### Post by steve101101 on 2007-03-02
this site provides nice screenshots and COMPLETE install instructions

---

### Post by Shay Stephens on 2007-03-02
> **steve101101 said:**
> ***WARNING NOT SECURE***
Warning heeded, ignoring posts as dangerous.

---

### Post by steve101101 on 2007-03-02
it means that you computer can be edited by any user without a password and loses security over the internet. as said earlier...

> **slayerboy said:**
> If he goes online at all, he runs a real risk of getting his system fubar'd...seriously, that's why Linux is more secure because you HAVE to do this.  If he's running this way, he's no better off than using windows.

---

