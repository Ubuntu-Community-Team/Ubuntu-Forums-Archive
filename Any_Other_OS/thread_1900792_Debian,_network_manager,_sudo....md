---
title: "Debian, network manager, sudo..."
date: 2011-12-27
forum: Any Other OS
---

### Post by sunfromhere on 2011-12-27
[SIZE=1]I installed Debian only to find out that for some reason CD1 comes without network manager. So, cannot connect to the Internet.

As I am multibooting, I had the idea of downloading the network manager .deb and just installing it. I opened the terminal, wrote: sudo dpkg -i longname.deb only to get:
sudo: command not found

Then I tried without sudo, only to get:
this command requires root privileges.

Tried with su, and I got the list of options for incomplete command.

What is this witchery? :) Why is sudo not found? How am I to connect to the Internet on Debian? How am I to install anything if sudo is not found?[/SIZE]

Ok, I just found [this thread]("http://ubuntuforums.org/showthread.php?t=1824438&highlight=debian+network+manager"), I'll just have someone download the DVD for me and reinstall, seems the easiest thing to do... But why is sudo command not found? Seems a bit odd...

EDIT2: I managed my way trough "su root some command", but for any and every command I try, I get: command: cannot execute binary file. This will be interesting....

EDIT: There seems to be lots of DVDs too. This Debian Network installation, how does it work? If I install just basics (you know, network manager... :) ), how big is it? This is very important to me as I'm not on unlimited plan. Anyone had experiences with this?

The question nr2 still remains:

Another thing, since multiboot - Ubuntu's loading screen looks like a badly messed up graphics card gone wild (when Ubuntu was the only os, it was a nice purple screen). Once logged in, everything is normal. Anyone had situation like this?

---

### Post by mips on 2011-12-27
> **sunfromhere said:**
> I installed Debian only to find out that for some reason CD1 comes without network manager. So, cannot connect to the Internet.

How do you connect to the net, via wired lan or wireless lan?
You should still be able to configure the network from the terminal or via a text editor.


> **sunfromhere said:**
> [SIZE=1]Tried with su, and I got the list of options for incomplete command.

What is this witchery? :) Why is sudo not found? How am I to connect to the Internet on Debian? How am I to install anything if sudo is not found?[/SIZE]


Debian does not treat it's users like idiots and restrict root access. During setup you should have been prompted for the root password so I think you should just be able to type 'su' followed by 'enter' which will prompt you for the root passwords and then you can execute any command without the need for sudo. It's been a while since I installed debian so i could be wrong.

Are you running debian stable or testing? What desktop environment do you plan on using? Another option is to have a look at Crunchbang (brilliant distro) which come in Openbox & XFCE versions (32 & 64bit as well). It's Debian preconfigured for you so it might be worth your while as it will save you some bandwidth and you will have a system up & running in no time. You can then add gnome, kde etc if you have a need for those. THey also have a brilliant forum for support and the folks over there are uber friendly. Just an idea.

---

### Post by gusnan on 2011-12-27
[SIZE=1]> sudo dpkg -i longname.debOn a system not using sudo (like debian [/SIZE][SIZE=1]default[/SIZE][SIZE=1]) you can do this like this:

```
su -c "dpkg -i longname.deb"
```[/SIZE]

---

### Post by sunfromhere on 2011-12-27
> **mips said:**
> How do you connect to the net, via wired lan or wireless lan?
You should still be able to configure the network from the terminal or via a text editor.

Via wireless. Tried to configure it while installing Debian, but I got "wrong password" error (it wasn't)... Also it claimed "no wireless networks found" even though the modem is 50 cm from the computer. Plugged in a cable just now, any command I tried was a blank. I'll find some instructions for dummies and try again.

> **mips said:**
> Debian does not treat it's users like idiots and restrict root access. During setup you should have been prompted for the root password so I think you should just be able to type 'su' followed by 'enter' which will prompt you for the root passwords and then you can execute any command without the need for sudo. It's been a while since I installed debian so i could be wrong.

"su root" prompts for password, but then everything just gives me: /name of command/:cannot execute binary file.

> **mips said:**
> Are you running debian stable or testing? What desktop environment do you plan on using? 

Debian stable, 6 I think it was when I downloaded it. And I'm not quitting it until I have a working wireless network on that thing. :D

Back to reading!

---

### Post by mips on 2011-12-27
> **sunfromhere said:**
> 
"su root" prompts for password, but then everything just gives me: /name of command/:cannot execute binary file.

Have you tried logging in as 'root' itself with the password you specified during setup?

This should work and with the network cable you now have plugged in you should be able to install sudo and any other applications you require to get going.

---

### Post by sunfromhere on 2011-12-27
I did it - partially!

Once I 'configured' my cable network (ashamed to say I hadn't fully plugged in the cable...) it was easy to install missing stuff. I also understand what I did wrong with 'su' (I'm used to Ubuntu now, so it struck me odd to have root@computer for the whole session).

The wireless network took me some time (apparently it had to do with missing non-free firmware - installed them, rebooted, now it's working) BUT it's too slow. It feels like a dial-up modem. And it's acting up (f.e. I can open this forum, some other sites, but cannot open google).

Any ideas on this?

---

### Post by Lampi on 2011-12-27
How's the link quality? (iwconfig wlan0 should tell you that)

---

### Post by sunfromhere on 2011-12-27
Link quality: 70/70

I am now checking Ubuntu (where wireless works flawlessly) with Debian, and all these are the same:

iwconfig wlan0 gives the same info on both
lspci -k shows the same drivers are in use

The only difference is that Bluetooth works on Ubuntu, and on Debian is showing eternal disabled state (no way to enable it).

---

### Post by mips on 2011-12-27
> **sunfromhere said:**
> I also understand what I did wrong with 'su' (I'm used to Ubuntu now, so it struck me odd to have root@computer for the whole session).


That's what I was getting at.

---

### Post by sunfromhere on 2011-12-27
The wireless connection is now working at the same speed as in Ubuntu. I haven't done anything (only shutdown computer and went away).

Next question: how do I remove that awful sound Debian makes on login? :D

---

