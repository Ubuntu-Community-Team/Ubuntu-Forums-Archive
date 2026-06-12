---
title: "Home server - printing and file sharing"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by japis on 2007-04-25
Hi everyone,

I'm a newbie with Linux, but I want to set up a home server to do the following:

- Print server
- File server
- FTP server
- Web server

I have a PC (PIII, 192MB) with ubuntu server 6.06.

So far, I've managed to install the OS, install webmin on top of it (so I don't have to go to the basement where the server is every time I need to change anything) and configure Apache as the web server. Everything seems to be fine!

Now, I'm having trouble with the rest of server programs. I'm pretty sure this has been covered before, so if anyone could point me to a good howto, starting from the very beginning, that would really help me.

Some additional details:

Other PCs in the network: 1 laptop with vista and occasionally another laptop with XP
Printer: HP OfficeJet 4315 all-in-one


Thanks everyone!

---

### Post by Jussi Kukkonen on 2007-04-25
I suggest you install an ssh server instead of ftp if at all possible, and use scp/sftp to copy stuff there -- this is a lot more secure. If you still decide to go with ftp, there are a lot of alternatives. With ssh access you can do admin work on any of them, but as it sounds like you want a graphical UI, you might want to look at something that's supported by webmin, or *pure-ftpd* as it has a gtk frontend (that you can run remotely over ssh).

For print and file serving in a windows environment, you want Samba:  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba). There is a web config frontend for samba (don't remember the name) and webmin might support it... and there's always ssh if you need to edit a config file. (Yeah, I'm rooting for ssh -- it really is a great tool: just login to the machine remotely and do anything, you can even run GUI software remotely).

---

### Post by japis on 2007-04-25
Hi Jussi,

thanks for your response. I really don't know which is the best software for me to use, so maybe if I explain a bit deeper what I want to accomplish you can recommend something.

What I'd like my system to do is:

-Print server: not much to add here... a USB printer connected to my ubuntu box, waiting for print jobs to be sent.
- Web server: mainly to have a photo (and maybe video) album to share with family.
- file/FTP server: to move files to/from other machines. Maybe I could do without the file server, as this will be done occasionally, and FTP should be enough... Also for people to be able to add files to the photo albums...

So with this in mind... what can you suggest? I chose webmin because I liked the idea of having a remote administration tool, but I'm open to any suggestion.

Thanks again.

---

### Post by jmagsho on 2007-04-25
Another source of information I've found to be quite useful for Ubuntu in general (but it does have a chapter or two devoted to server installs) is a book called 'Ubuntu Hacks'.  It's readily available on Amazon and Borders.com...

---

### Post by mattmole on 2007-04-25
Hi,

Try going to the following address:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

At this website you can download either the PDF or look at the HTML server manual. I have used this before to setup an SVN server for managing sourcecode. 

I do know however that in this document there is information on SAMBA (file server), SSH server, FTP server, CUPS (print server)

I have used all of the above servers and administering them is quite easy. I tend to edit the config files directly. There are instructions for this in the document.

I hope that helps. Did you want your FTP server to be open to the wild world or just within your LAN? If within a LAN and your FTP port is closed to the internet then I would not be quite so concerned about using FTP rather than SCP. However, I do not use FTP *at all*, I use SCP and securely copy files between machines on my home network.

Also, another good resource I have found is [www.linuxreality.com](www.linuxreality.com) at the moment Chess is in the middle of a series of podcasts about home networking.

Matt

---

### Post by Jussi Kukkonen on 2007-04-25
> **japis said:**
> -Print server: not much to add here... a USB printer connected to my ubuntu box, waiting for print jobs to be sent.
- Web server: mainly to have a photo (and maybe video) album to share with family.
- file/FTP server: to move files to/from other machines. Maybe I could do without the file server, as this will be done occasionally, and FTP should be enough... Also for people to be able to add files to the photo albums...


I think you are going to need samba for the printer sharing anyway, so it would probably make sense to setup file sharing in samba too... I wouldn't open samba to the internet in general, so you might need ftp on the side. But if you meant that the picture uploading would happen inside your local network, samba can do that (and it's user-friendlier than ftp). I think you should read up and try the samba installation (getting windows and linux machines to communicate  can be a bit frustrating even with samba, but it's not impossible).

Web servers are like ftp servers: there are many to choose from and the feature sets vary widely. If you just want to serve static pages and do not need great performance, I think you should go with a simple one and not e.g. Apache (which is great but complex). Maybe lighttpd, webfs or thttpd (I haven't used any of these much so won't recommend -- any should be fine for static content, but they may have differences in ease of use)

---

### Post by japis on 2007-04-26
Hi everyone...

thanks for your suggestions. I think I'll start with samba, as it looks like it can solve two of my needs (print server and file sharing).

Apache seems to work fine, so I'll leave that as it is.

I'd still like people from outside my LAN (like my parents, friends,...) to be able to upload photos to my albums, so I guess I'll still need FTP or the like. But I'll leave that for later.

Thanks again!

---

### Post by sinaen on 2007-05-08
there are advanced clients or programs for your homepage that enable people to upload images :) like a picture-blog

---

