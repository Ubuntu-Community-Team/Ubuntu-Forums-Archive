---
title: "Windows won't accept Ubuntu password"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-10-02
I am able to see my Windows [98SE] computer from my Ubuntu computer, e.g., I can read and copy files. I can't see the Ubtunu computer from the Windows computer. 

Before I've accessed the Windows computer from the Ubuntu computer, the Windows computer sees only itself. However, after I've accessed the Windows computer from the Ubuntu computer -- and only then -- the Ubuntu computer shows up in the Windows computer's Network Neighborhood in a separate workgroup . 

If I double-click on the icon for the Ubuntu computer, Windows asks me for a password. If I give the only password I've ever used for either computer, Windows tells me it's the wrong password. I have a sneaking suspicion that if I could provide the right password, I'd have access to the Ubuntu computer from the Windows computer.

Two questions: [1] Why isn't Windows accepting the password? What is it asking for if it's not the only password I've ever used with either system? [2] How can I get the two computers into the same workgroup? Will drag and drop in Windows Explorer work? [I guess that's actually three questions!]

I feel like a blind man trying to get to know a new neighborhood. Help is greatly appreciated.

Sincerely

---

### Post by 505 on 2007-10-02
The way networking works in Windows 98 - let's just say it's not very good. For example, when you access a network source from within Windows it will only ask for a password, not the username. I expect that Ubuntu also wants to have a username to match the password with. You might try to change the username with which you log into Windows (although you never actually log in, it just boots and never asks for a password. There is a place where you can change it)

As for the workgroup, this is a setting on your Ubuntu box. Open the file /etc/samba/ smb.conf in a text editor (in admin mode) and change the line 'workgroup = SOMEHTING' to the desired workgroup. Then reboot samba (sudo /etc/init.d/samba restart)

---

### Post by leggament on 2008-03-14
I am having the exact same problems in Hardy. The work group was resolved after putting the workgroup name in through the network settings and rebooting the computers. The file /etc/samba/ smb.conf showed the workgroup like the change that the last post (505) showed. I still have a problem logging on from my windows machines to the ubuntu computer.Any help would be appreciated.

---

### Post by joshrobinson on 2008-03-14
you have no password, thats the problem

```
sudo smbpasswd -a username
```
where it says username put your username
put in your sudo password, then it will ask for the password for your samba password

then

```
sudo /etc/init.d/samba restart
```
this will restart samba

try it out now

---

### Post by iansane on 2008-03-14
Like the above post says, I think you have to set up the password in samba, I had the same problem with XP where it asks for username and password. Don't remember but I think ubuntu needs both, kinda like setting a username and password for an ftp. It's different than your normal log in and has to be set up as a samba user. Actually I had the same problem with three computers. One ubuntu, one windows, and one debian. Also there was something in another post about Gutsy defaulting the name of the workgroup to workgroup when you restart if you don't change it in the config file. It's ok if all your windows use workgroup as the name.

---

### Post by leggament on 2008-03-15
I read this thread and following it solved my problem  "http://ubuntuforums.org/showthread.php?t=719147". 
The thread told me to edit this "/etc/samba/smb.conf" by changing the "; security = user" line to "security = share" note the semicolon has been removed

Part of the file /etc/samba/smb.conf 

 ####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

Doing the edit of that line fixed the problem I can now go to my files from a Windows computer to my Ubuntu computer.  Now I am wondering if I can make my system more secure by changing the line back to ";   security = user"  and getting a samba password.
The thread seemed to imply that leaving that line changed to "security = share" could leave my machine at risk.  Any thoughts?

---

### Post by bigtel on 2008-03-16
Thanks to 'joshrobinson' for his tip. This simple command has now stopped the annoying password prompt appearing. I spent hours trying to figure out what the user / password could be. Now I can communicate between my XP and Ubuntu systems on 2 different PC's

Once again thanks.

BigTel:)

---

