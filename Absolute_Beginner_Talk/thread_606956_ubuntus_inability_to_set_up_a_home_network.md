---
title: "ubuntus inability to set up a home network"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by antony11 on 2007-11-08
I know Im new to linux and my knowledge is very limited. But after spending near enough a week going through several howto files and examples and asking several questions on this forum I am no nearer to getting my linux box active on my home network. I have noted that several people are having issues with setting up networking and Im beginning to wonder if this is just our lack of understanding or is it a bug?
My issues are as follows:
1. Any setting I put into network settings are lost when I reboot.
2: Sometimes I can access as far as going through the places > network > windows network > (my network) then I get the following message:-  "The folder contents cannot be displayed ...."
3. Sometimes I get as far as  places > network > windows network and then I get a message window up asking me for a password. Despite giving the only password presently active on this box it just keeps showing the same window asking for password.

Yes I have installed samba and yes I have setup a smb user and password. IP addresses are via dhcp.

I know this community is great and the advice is freely given and appreciated but Ubuntu is proving (at least for me) to be extremely user UNFRIENDLY. I know all you great folk out there are being helpful but I think what some of us need is either someone who is an expert in networks but can put it in beginners language or a dirty great big hammer :)

one VERY frustrated newbee

ps Would I find network set up any easier with a different version of linux? (I currently have ubuntu 7.10 installed)

---

### Post by BrendanM on 2007-11-08
First off, I would not claim to be an "expert in networks" but based on the password issue, it sounds to me like maybe there's a permission issue on your windows boxes. Are you using simple file sharing, or have you configured passwords?

Also, you might try either pyNeighborhood or xSMBrowser, they're both programs designed for accessing samba network shares, and you might have better luck than just using Nautilus. Just some suggestions, sorry you're finding it frustrating.

Have you installed "winbind"? I don't know whether it's necessary or not, but I remember doing it as part of setting up my network.

---

### Post by bodhi.zazen on 2007-11-08
Is your problem with setting up your networking or with samba shares ?

If with networking, what network card are you using, wired or wireless ?

If with samba, can you check the settings on the windows side ? Can you connect with a windows client ? Normally the samba client works out of the box.

If you installed samba, that is the samba serer so that you may share ubuntu -> windows.

---

### Post by candtalan on 2007-11-08
Which ubuntu version are you using?

As I recall it from a distant past when I wanted to network with windows machines (XP) I found  it was  essential to have a user sign on into the xp machines, which btw had to be network capable (XP professional not xp home?). My practice early on was to have no sign-on into the xp machine/s, but this apparently gave the machine an identity confusion which networking attempts discovered.

And of course I had to set up windows shares too

Your frustration (sympathies!) reminds me of how I felt in a very similar situation. I am glad to say that the more I left windows behind, the more relaxed I felt. My experiences with my years of windows use made believe that if ever I thought windows was friendly, it was in fact a false friend.

good luck.

---

### Post by swoll1980 on 2007-11-08
What network settings are you trying to change. I had problems with my DNS address being reset, but found a solution that has worked good. Enter the settings in the network manager then
```
sudo chattr +i /etc/resolv.conf
```
All the network settings are saved to txt files so this command should work with any setting that is reseting just change the path in the command to the file you want to lock to unlock switch the + to a                  -

---

### Post by antony11 on 2007-11-08
Ive just installed xSMBrowser. Having done so and clicked on the "samba config" text in the window the terminal scrolls through a little text and the final lines are as follow:

spawn smbclient -N -L DAD-DESKTOP -I 192.168.1.200 -W STARTREK
Domain=[STARTREK] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_LOGON_FAILURE

Im presuming that this is telling me where my problem lies. However I dont know how to resolve it.

---

### Post by ukripper on 2007-11-08
Guide -
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

---

### Post by antony11 on 2007-11-08
I think I should point out that I have 2 issues and I constantly seem to be confusing them. First off I cant see any box on the network - so that is a network issue (?)
second I cant even see any folder that I have set up on the linux box to be shared. I presume that I should be able to see them on the network and Im also assuming that this is a samba issue?

---

### Post by ukripper on 2007-11-08
> **antony11 said:**
> I think I should point out that I have 2 issues and I constantly seem to be confusing them. First off I cant see any box on the network - so that is a network issue (?)


Let's start with your first issue.

What box you are talking about can your provide screenshot?

---

### Post by antony11 on 2007-11-08
> **bodhi.zazen said:**
> Is your problem with setting up your networking or with samba shares ?

If with networking, what network card are you using, wired or wireless ?

If with samba, can you check the settings on the windows side ? Can you connect with a windows client ? Normally the samba client works out of the box.

If you installed samba, that is the samba serer so that you may share ubuntu -> windows.

q1 both
q2 wired network card
q3 Have yet to learn how to :(

---

### Post by antony11 on 2007-11-08
> **ukripper said:**
> Let's start with your first issue.

What box you are talking about can your provide screenshot?

box = computer
I have a small network of 3/4 pc's 
box 1 (this one) is a dual boot ubuntu/vista
box 2 vista
box 3 xp
box 4 will be a linux server once set up (assuming I ever get this one done first)

---

