---
title: "How can my son upload/download files from overseas to home PC?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-08-22
My teenage son soon heads out on a year-long student exchange to South America. He will have regular access to high speed internet.  He would like to have access to our home LAN both to transfer images from his trip and to get mp3's his brother wants to send him. 

Our home LAN consists of:[LIST]
[*]XP gaming desktop (newer)
[*]Ubuntu 7.04 laptop (older)
[*]Ubuntu 7.04 desktop (old)
[*]Ubuntu 7.04 server (really old)
 *  Note: This is not a server in the truest sense of the word.  I've installed the server version and have essentially used it as a local repository (music, images, homework) so the family can access their files from any computer in the house.  I had SAMBA setup so WIndows boxes could access files and this setup worked like a charm within the home.*[/LIST]

***What is the easiest and most secure way to setup my "server" so family members can access files from outside of the home?* **I don't intend on using this computer as a web or mail server nor will it be public.  Just a basic box with files that can be accessed remotely
 by the family.

---

### Post by jfinkels on 2007-08-22
> **Ian-on-the-Trent said:**
> My teenage son soon heads out on a year-long student exchange to South America. He will have regular access to high speed internet.  He would like to have access to our home LAN both to transfer images from his trip and to get mp3's his brother wants to send him. 

Our home LAN consists of:[LIST]
[*]XP gaming desktop (newer)
[*]Ubuntu 7.04 laptop (older)
[*]Ubuntu 7.04 desktop (old)
[*]Ubuntu 7.04 server (really old)
 *  Note: This is not a server in the truest sense of the word.  I've installed the server version and have essentially used it as a local repository (music, images, homework) so the family can access their files from any computer in the house.  I had SAMBA setup so WIndows boxes could access files and this setup worked like a charm within the home.*[/LIST]

***What is the easiest and most secure way to setup my "server" so family members can access files from outside of the home?* **I don't intend on using this computer as a web or mail server nor will it be public.  Just a basic box with files that can be accessed remotely
 by the family.

You can enable port forwarding on your router, and have your son use SSH to access the command line of one (any) of the Ubuntu machines, and use SCP to copy files over the net. That's one easy/secure way.

---

### Post by jfinkels on 2007-08-22
Or you can try to work out your own personal VPN, but that may be quite a bit more complicated:

[https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer)
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

---

### Post by Ek0nomik on 2007-08-22
SSH will do the job for sure.

[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

If he is on Windows he can use WinSCP, if he is on Ubuntu he can do it via command line OR he can also do it graphically using Nautilus (your default file browser)

---

### Post by Ian-on-the-Trent on 2007-08-22
He'll most likely be using a Windows box while away.  I'm not sure if he will be able to install software at his end...at least initially.  For the near term there will be a language barrier between him and his host family.  He doesn't yet speak Spanish. I can only assume that the Windows box will be in Spanish,.

As well, I am concerned about getting hacked.  I'm on a cable modem with a virtually static IP. Is there any one method that is more secure than another?

---

### Post by Ek0nomik on 2007-08-22
> **Ian-on-the-Trent said:**
> He'll most likely be using a Windows box while away.

I am concerned about getting hacked.  I'm on a cable modem with a virtually static IP. Is there any one method that is more secure than another?

Well SSH is a secure way of transferring files.

You can tweak SSH quite a bit to make it even more secure if you are worried:

[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)

[http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/](http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/)

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by Ian-on-the-Trent on 2007-08-22
(Thanks for replying so promptly)

If using SSH, will he still have to install software at his end or will he be able to open up a browser and simply login to my server?

---

### Post by kvonb on 2007-08-22
Install "putty" on your son's laptop before he goes, then he simply runs that and connects to your server (install openssh-server through synaptic or apt-get).

Also, I would suggest if you are going to use ssh, that you change the default port (edit /etc/ssh/sshd_config) from 22 to something much higher.

The reason being that script kiddies will try and try to crack the password, as port 22 is a common one to attack.

If it's not easy to find, then you will avoid a lot of problems.  Not that they might get in, but all the traffic and logging of failed attempts bogs a slow machine down.

With putty, you can save an ssh session so all he has to do is double click on the connection, makes it very easy.

You could alternatively install apache web server and use directory passwords, it's quite easy to do and can then be accessed via a web browser.

There are plenty of how-tos on the forum.

---

### Post by Ek0nomik on 2007-08-22
He would want to install WinSCP to transfer files from his Windows box to your Ubuntu box.

[http://winscp.net/](http://winscp.net/)

Dealing with the security kvonb mentions is provided in the links I gave you.

---

### Post by Ian-on-the-Trent on 2007-08-22
> **kvonb said:**
> Install "putty" on your son's laptop before he goes, then he simply runs that and connects to your server (install openssh-server through synaptic or apt-get).

Actually, he'll be using the host family's computer and not his own.

> You could alternatively install apache web server and use directory passwords, it's quite easy to do and can then be accessed via a web browser.

Now, this is more in-line with what I have been thinking of.  Is installing Apache easy enough for a noob?

---

### Post by Ek0nomik on 2007-08-22
> **Ian-on-the-Trent said:**
> Now, this is more in-line with what I have been thinking of.  Is installing Apache easy enough for a noob?

```
sudo apt-get install apache2
```

Once finished, open Firefox and type: [http://localhost](http://localhost).  If you want to change the files Apache serves navigate to:  /var/www.  You'll probably see a default folder called apache2-default and an index.html page.

Protecting Directories w/ Apache:

[http://www.ilovejackdaniels.com/apache/password-protect-a-directory-with-htaccess/](http://www.ilovejackdaniels.com/apache/password-protect-a-directory-with-htaccess/)

[http://www.apacheweek.com/features/userauth](http://www.apacheweek.com/features/userauth)

[http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html)

[http://linuxhelp.blogspot.com/2006/02/password-protect-your-website-hosted.html](http://linuxhelp.blogspot.com/2006/02/password-protect-your-website-hosted.html)

[http://www.modwest.com/help/kb1-32.html](http://www.modwest.com/help/kb1-32.html)

Cheers!

---

### Post by Ian-on-the-Trent on 2007-08-22
I'll give it a whirl.  Thanks for all your help Ek0nomik, kvonb, & jfinkels.

Cheers!

---

### Post by Ek0nomik on 2007-08-22
> **Ian-on-the-Trent said:**
> I'll give it a whirl.  Thanks for all your help Ek0nomik, kvonb, & jfinkels.

Cheers!

That's what were paid to do... er... rather... watching American Beauty with a laptop in front of me.  :)

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
[SIZE="5"]Make shur you can do this with out pissing of you ISP kuss if your residential they don't like you haveing file server and it may be illegal[/SIZE]

---

### Post by daveshields on 2007-08-22
The more I learn about the Ubuntu community the more impressed I am. For example, witness the quality of the  prompt responses to this question. Indeed, I was so impressed that I have just written about it in my blog. Ubuntu has been the subject of most of my recent posts.

See "Sell support? Why not give it away for free?" at [http://daveshields.wordpress.com/2007/08/22/sell-support-why-not-give-it-away-for-free/]("http://daveshields.wordpress.com/2007/08/22/sell-support-why-not-give-it-away-for-free/")

---

### Post by Ek0nomik on 2007-08-22
> **<<joe>> said:**
> [SIZE="5"]Make shur you can do this with out pissing of you ISP kuss if your residential they don't like you haveing file server and it may be illegal[/SIZE]

There is nothing illegal about this.  His son isn't uploading illegal content (well, he could be, but I don't think that's their intention).

> **daveshields said:**
> The more I learn about the Ubuntu community the more impressed I am. For example, witness the quality of the  prompt responses to this question. Indeed, I was so impressed that I have just written about it in my blog. Ubuntu has been the subject of most of my recent posts.

See "Sell support? Why not give it away for free?" at [http://daveshields.wordpress.com/2007/08/22/sell-support-why-not-give-it-away-for-free/]("http://daveshields.wordpress.com/2007/08/22/sell-support-why-not-give-it-away-for-free/")

Glad I could be part of your blog post.  :P

---

### Post by eentonig on 2007-08-22
Btw. Some random hints to take into account.

- If you're behind a NAT router (most likely, since you use several computers), make sure you configure it to forward requests to the server in question. You need to configure port-forwarding. 
- Most likely, you get random and changing IP addresses from your provider. So your son won't know where to connect to. The easiest to overcome this, is to install a Dynamic dns client that updates and translates your current public IP to a well known name. ( I use dyndns, but there's an howto for another client in the community docs)

---

### Post by hyper_ch on 2007-08-22
Well, whether something is illegal or legal depends on the country you are in. For you there are two countries to consider: The one you live in and the one your son will go to. What might be legal in your country, could be illegal in the country where your son goes to.

How to share?
I tend to think the most simple way is using SSH and a graphical client.

(1) Install openssh-server
```

sudo apt-get install openssh-server

```

(2) Port forwarding
On the router you have, forward port 22 to the machine you just have installed openssh-server to

(3) Client
- In windows a nice graphical client is Winscp: [http://winscp.net/](http://winscp.net/)
- In linux I use Konqueror (enter something like this:    fish://user@server   --> see below)

(4) Login
Adress/Server: Either your son must know your public IP address or you use a dynamic dns service such as [www.no-ip.com](www.no-ip.com) or [www.dyndns.com](www.dyndns.com)
User/Pwd: This is your normal user login on that machine where you have openssh-server installed.

(5) Test
Make a test from outside your network

That's it :)

---

### Post by StooJ on 2007-08-22
The trick is being unable to install things on the computer in South America.

Sure, [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") & [WinSCP]("http://winscp.net/eng/index.php") would be ideal, secure and easy to use (I use both myself), but they require installing software on a client PC.

I'd say apache is the best way to go in this case, since it won't require any software on the client machine in South America (apart from a web browser of course) and can be easily stuck behind a password.

Changing the default ports is definitely a good idea, a) for the script kiddies and b) for ISPs, since some of them tend to block popular ports for hosting a server. It's maybe worth skimming over the T&Cs just to check as well, and if they have a problem with a server, change ISPs :D

[No-IP]("http://www.no-ip.com/") is the DNS service I use, you can set up an account and they'll redirect any traffic from yourusername.no-ip.org to your server IP. It keeps track of your IP via a handy linux wee client which is in the Ubuntu repositories.

---

### Post by hyper_ch on 2007-08-22
Ok, didn't consider about not being able to install software ;)

I also use no-ip and the OpenWRT software on my router has already a client integrated ;)

---

### Post by steve.horsley on 2007-08-22
Another vote for SSH here. You will need to forward port 22 to the SSH server at home HQ. 
FileZilla (freeware) is a very useable Windows FTP and SFTP client. 

Make sure you have strong passwords on your SSH server because there are SSH password guessing bots out there. Consider using a port other than 22, e.g. 22222 to avoid most of these bots. Also consider using /etc/hosts.allow/deny or a firewall to limit the IP adresses that can connect to the server. Also consider using certificates for authintication, although this may be more complicated to set up.

---

### Post by Ian-on-the-Trent on 2007-08-22
Wow! Many options and I do appreciate all the input.

The overriding condition...he very likely ***won't ***be able to install software.  This is why using a browser with username/password is so attractive.  

What is the best way to set up Apache for this? Does it make sense to require monthly password changes? Is there a huge security trade-off by using Apache instead of the largely recommended SSH/Putty combo?

[I]
**NOTE: **My isp does not like home servers for residential users. However, it has to date overlooked this from subscribers since the ISP has moved away from bandwidth limits.

Can two setups be used?  Could I use SSH for when I travel and need access to my server as well as Apache for my son?  I would need access to the files he needs PLUS files related to my work.[/I]

---

### Post by steve.horsley on 2007-08-23
Sorry, I can't help with the apache setup. Hopefully someone else here can. As with SSH, it might be a good idea to run the server on a high port number instead of the usual port 80, to reduce the likelyhood of a bot finding it.

You can certainly run an SSH server as well as a web server. No problems there - the two would be completely independent.

---

### Post by ianhaycox on 2007-08-23
Another alternative is to use something like Flickr or Picasa to store your images. Just a web browser needed to upload and download your images.

For the mp3's you could try something like [XDrive]("http://www.xdrive.com/") or similar. I've not used them but basically they are free online web storage I believed accessed again by a browser.

Finally, maybe get a cheap domain name and hosting then just use ftp to upload/download into a protected directory. Most hosting companies provide a control panel to allow protected www access into a specific directory. Check the T&C on data storage, Yahoo just changed thiers to prevent this.

I realise the three options above mean using an intermediate 'storage' point, but it saves opening ports at home and risking a security problem.

Ian.

---

