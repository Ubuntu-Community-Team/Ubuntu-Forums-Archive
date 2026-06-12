---
title: "Mounted network drive just hangs"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-02-19
Hello folks,

I need to access a server. In the old days I used WinSCP. I connect using SSH and I prefer a visual format for the purpose I have now. 

I mounted a network drive to my Ubuntu desktop and set everything up correctly. I can connect to it about 10% of the time without a problem. However the other 90% of the time - after I click on the icon all it says is "Opening [network drive name]" and it sits there indefinitely until I close it out. 

There is little if any consistency between when it does work and when it doesn't. One of the problems is the fact that it DOES work - it leads me to believe I have done everything properly and there is something really weird going on.

Any ideas? Is there any other visual explorer-like program I can use? 

Thanks for any ideas - this is one of the last things keeping my laptop around. My experience with Ubuntu in the past month has been nothing short of incredible!

---

### Post by justleen on 2008-02-19
what kind of server do you connect to? samba? nfs?

You say you used WinSCP, thats for ssh.. you cant "mount" an ssh drive (well, you can, with [sshfs]("http://fuse.sourceforge.net/sshfs.html"), works like winscp)

---

### Post by Nutopia on 2008-02-19
I'm not certain off hand about the details of the server except that it runs Red Hat. 

The "Connect to Server" feature on the Ubuntu desktop allowed me to specifically create an  SSH connection, but it just hangs.

I tried installing sshfs from the package manager but not sure what it did..?

---

