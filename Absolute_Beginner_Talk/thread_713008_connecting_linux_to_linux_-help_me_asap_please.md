---
title: "connecting linux to linux -help me asap please"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by nav882 on 2008-03-02
Hi all,
I want to know how we conect linux machine from another linux machine remotely(This is basically for connecting home to office computer).In windows i used putty and used the following steps to connect it.But how do i do it in linux please advise with steps.
steps to connect from windows:
Steps to create VPN connection

1) go to mynetowrks , click on view connection, click on Create connection
2) select Connect to network (using VPN) click on next
3) select VPN connection click next
4) Give ip address 61.85.76.56 and open putty and give my system ip i.e,26.0.0.45 which is our internal networks ip and
i can just give username and password and started working remotely.Please advise how to do the same in linux.Thanks in advance.

---

### Post by Mud.Knee.Havoc on 2008-03-02
You can use ssh to connect to a remote computer, or if you want to mount a remote system as if it's a local directory (so you can even drag and drop files between remote/local computers), you can do this with sshfs.  [Step-by-step at Ubuntu Geek]("http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html#more-44") or [helpful discussion here]("http://ubuntuforums.org/showthread.php?t=707121&highlight=sshfs"), or explanation of sshfs and instructions [here]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/").

I've also played a bit with [Hamachi]("https://secure.logmein.com/products/hamachi/vpn.asp"), which is interesting if you want a vpn but have to deal with dynamic ips (hamachi logs you on no matter which ip you have, and will facilitate a connection).

I'm not really sure exactly what your goal is for the connection, so can't offer any more suggestions.

EDIT: I just noticed that putty's been ported to linux...

---

### Post by nav882 on 2008-03-02
Hi,The connection that we havein office is a static ip.And we use linux machines there.So my query is simple how do we connect my home machine which also has a linux os on it to my office machine provided with the above details.

---

