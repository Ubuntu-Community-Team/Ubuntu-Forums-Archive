---
title: "Ubuntu Networking - Is there a simple description?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by getglenn on 2005-11-10
i'm looking for a HOWTO or article that describes, in simple terms, how a network can be used to connect two Ubuntu PCs

after reading many Howtos and guides i am little the wiser!

many mention SAMBA, but i just want to connect 2 PCs, each running Ubuntu. What is the DEFAULT network file system for Ubuntu? i assume there is one?

the two computers are connected by CROSSOVER cable and i can PING from each one successfully, 

i don't know how to set them up so i can browse the files from Nautilus

i assumed it would be as simple as using Windows, but i am obviously missing something

---

### Post by garciadc on 2005-11-10
I have a home network, most comps w Ubuntu, and I just make which folers I want to be shared by right-clicking file and selected "Share folder" in Nautilus. I go under Places>Network Severs to acsess Linux and Windows comps. Then I log in with appropriate user name and password and I can read the files (I mainly share my music).    I guess if you want to be able to modify files then you can change their permissions.

---

### Post by getglenn on 2005-11-10
thankyou for that info, it was exactly the sort of thing i was after...

however, when i click on a folder to SHARE it, it offers me the "use SMB" option

i thought SMA was only for connecting to WINDOWS networks?

regards glenn

---

### Post by n0ah420 on 2005-11-10
SAMBA can be used on any platform.  Make sure that samba/smbfs is installed so that you can share properly.  You can search for these in synaptic.  Once these packages are installed sharing the directories should work fine.  Look at /etc/samba/smb.conf for more configuration options.  NFS is also another option for sharing directories however the syntax is a bit more abstract.

---

### Post by mlomker on 2005-11-10
SMB is primarily used in Windows, but it's easier than the traditional linux method of NFS.

---

### Post by getglenn on 2005-11-11
[QUOTE=mlomker]SMB is primarily used in Windows, but it's easier than the traditional linux method of NFS.[/QUOTE]

thankyou
for your simple, but eloquent explanation... i have been reading so much about networking that my head is about to explode, so i'm really slow at absorbing some of the info and getting a clear idea of the concepts involved

so, is SMB the preferred/recommended Ubuntu method, or does it depend on the user's needs?

---

### Post by Herman on 2005-11-11
I am finding SSH to be a good way of networking between the four dual boot computers we have on our LAN. It's easy to set up, you can already connect to an SSH server by default, but at least one (or more), of the computers on your LAN needs the 'Open SSH server' package and 'SSH' package. You can use 'Synaptic to get those from it's 'networking' category. 
Then you just click 'Places', 'Connect to Server', and a window will appear on your desktop called 'Connect to Server'. You set the 'Service type' to 'SSH', enter the I.P. address of the other computer in the 'Server' feild. (You find that out by typing the following into a terminal in the other computer). ```
ifconfig
```
Then you type the number 22 in for 'Port', and /home/username in for 'folder', and a username for a user of the other computer for a name for your connection, (hostname).Then click the 'connect' button. If you are lucky, you'll get a 'Question' like 'the identity of the remote computer is unknown', then you click the 'log in anyway' button. If it asks for a password to log in to the remote computer, you give the password belonging to the username you used earlier. If you ticked the 'save password in a keyring' tick-box, it might ask for your password for opening the keyring, you provide your password for your computer you are using now. (That you are connecting from). 
After you do it the first time, then everytime after that your password will be remembered in the keyring and it doesn't keep asking so many questions, so it's very quick and easy from then on. 
What I like about it, too, you don't have to edit text files and maybe make changes to your computer's security you aren't sure about.:smile:   (Herman)

---

### Post by n0ah420 on 2005-11-11
See this thread:

[http://ubuntuforums.org/showthread.php?t=76647&highlight=samba]("http://ubuntuforums.org/showthread.php?t=76647&highlight=samba")

It will show you how to set up smb networking.  I wouldn't say its preferred but its the most common method becuase of its Windows compatability.

---

### Post by mlomker on 2005-11-11
[QUOTE=getglenn]so, is SMB the preferred/recommended Ubuntu method[/QUOTE]

Yes.  The link that Noah provided is a good one.

---

### Post by Stew2 on 2005-11-12
Hello, I also have a similiar situation. I am trying to share my home folder in ubuntu with my network of 3 XP machines. I shared the home folder on the ubuntu machine and it prompted me to install Samba before it would allow me to share it, which I did.. or I should say it did it for me. Now I can see the ubuntu machine on my network, but when I try to access it I get a username and password box. When I type in the ubuntu machines username and password the username box changes to the name of one of my XP machines and it rehighlights the password box. The only password I have for the ubuntu machine is the one that I assigned when I set up my user info at the time of install, does Samba want some other password or did I just goof something up? I hope this is related enough to go in the same thread.:confused:  Thank you for any help you can give me.

---

### Post by mlomker on 2005-11-13
[QUOTE=Stew2]Thank you for any help you can give me.[/QUOTE]

Did you follow the link on post #8?  Ask your questions on that thread if you have problems.

---

### Post by n0ah420 on 2005-11-13
If you are having password issues you may want to run the smbpasswd program to set one for your username.  Then try logging in again, however to reiterate mlomker, try the link above for a clear description of SMB networking.

---

