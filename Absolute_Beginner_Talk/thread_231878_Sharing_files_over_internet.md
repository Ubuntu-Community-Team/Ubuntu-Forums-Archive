---
title: "Sharing files over internet"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Kibner on 2006-08-07
My Ubuntu box is at college, but I go back home on the weekends where I have access to a Windows XP machine.  I want to be able to share files between both of the computers.  What programs would I need to do this?  Should I use Samba, set up a ftp server, or something else?

---

### Post by orb9220 on 2006-08-07
Well if they are smaller than 10 megs I just use gmail and send as attatchments. If they have .exe in filename just rename them .exe.bak extension then can rename after retrieval.

That just a quick and dirty way. For more info I think SSH'ing into the box is what I see people discussing.

---

### Post by saracen on 2006-08-08
You can set up a guest account - or if you want you can set up one account per user.  Just go into System -> Administration -> Users and Groups.  After that have them download an SCP client like WinSCP which they can get from [here]("http://winscp.net/eng/download.php").  Then they can connect to your computer and login with the account(s) that you created.  You need to give them your computer's IP address for them to connect.

EDIT:

I thought you wanted to share files with your friends.  In this case all you need to do is figure out the IP address of ur machine at college and then use WinSCP to connect to it using your regular username and password.  You have to install the openssh-server program on the college machine to get the server running.

---

### Post by Kibner on 2006-08-08
Ahh, thanks for the info!  Will start messing with all of that good stuff in the morning.

---

### Post by Endolith on 2008-05-14
Giving SSH access to someone isn't great because it lets them see your entire filesystem, though.  What's the best way to just share selected folders (maybe with an upload folder or a few folders that they can modify but others that they can only read) without giving them a shell or access to the entire system?

---

