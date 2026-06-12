---
title: "[SOLVED] FTP folder in Nautilus is empty!"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2008-04-02
I'm trying to login to my ftp server (hosted by GoDaddy) and every time I use Places > Connect To Server and then fill in my ftp information under the FTP (with login) dialog I end up with a blank window.  I'm prompted for my password and I can see my ftp address in the Nautilus address bar, but the folder is empty.  However, when I login to the server through Firefox, using the same address, username, and password, I see all of my files.  What's going on?

-Mike

---

### Post by mikeserv on 2008-04-02
Bump.

---

### Post by mikeserv on 2008-04-02
Figured it out.  I don't know if this is common protocol, but apparently when I log into my ftp server I log into the server not in the "/" folder, like I was putting in the Connect to Server dialog, but into the /username/ folder.  I'll explain.

When I first opened the Connect to Server (under Places > Connect to Server) dialog I chose the FTP (with login) selection in the Service Type: dropdown.  I next filled in the Server field with my domain and left Port empty (for a passive connection, I hope).  Here's where I went wrong, though: for the Folder field I entered "/".  I then filled in my username and chose a name for the connection.  Then I clicked "Connect."  

After going back to Places > and choosing my new connection I would be presented with a dialog for entering my password, and, having filled that in, I would then see a nice, empty folder with my domain name in the location bar.  This was confusing, and, after double checking that my site was still there in Firefox, I tried it again.  Same thing.

So I got fed up and downloaded FileZilla.  I was able to connect and see my files no problem, but I noticed a folder in the path that I had never seen before.  My site wasn't "/stuff/on/server" it was "/username/stuff/on/server".  So I had a thought.

I went back to the Connect to Server and changed my Folder from "/" to "/username/" and, voila, there was all my stuff!

Again, I can't be sure if this is common practice, I just know that if anyone else uses GoDaddy and wants to access their FTP server through Nautilus they'll have to fill in their username in the path.

-Mike

---

### Post by amaroKer on 2008-04-02
i have the same problem.  It seems impossible to actually mount or browse an FTP server using Nautilus in Ubuntu.  Help anyone?

PS.  Is there any use for 'Network' under 'Places'?  It appears to only work with Windows networks, which I find to be 100% useless.

---

### Post by mikeserv on 2008-04-02
Are you trying to mount an SFTP server (one running ssh) or an FTPS server (FTP over SSL)?  Of course the former is the preferred method, as SSH is super secure and it rocks, but this post refers to FTPS, as far as I know.

For SFTP look into sshfs, I use it for all three of the computers on my home network and I love it.  One of the computers is a Vista machine (my wife likes it, what can I say?) and, with a few open-source proggies I found on the net, it SSHes with the best of them.

Anyway, try doing what I posted above, maybe it'll work.

-Mike

---

