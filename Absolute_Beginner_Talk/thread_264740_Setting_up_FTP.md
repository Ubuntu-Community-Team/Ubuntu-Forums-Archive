---
title: "Setting up FTP"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Varz on 2006-09-25
I'm new to linux and I am having some problems setting up vsftpd plz help.

I've been using Filezilla in windows and I can connect to the server through my webrowser, when I connect a popup window will appear where I can enter my username and password.  This does not happen in vsftpd.

When I try to connect to the server it says that the server does not allow anonymous connections and it doesn't allow me to enter my username or password.

Is the only way to access FTP through a ftp client program?

---

### Post by Kobalt on 2006-09-25
Hi,

You can access a FTP with Nautilus : Places > Servers (or something like this, I'm in KDE). Then you can configure the login/pass (and other stuff) of your FTP and a folder icon will appear on your desktop, allowing you to browse your FTP. 
I prefer using a dedicated app though. I use gFTP, but you can also use proftpd. You can easily install them with Aptitude : 
```
sudo aptitude install gftp
```
```
sudo aptitude install proftpd gproftpd
```

Unfortunately, I have never used vsftpd so I can't help you on using that particular app, but you should be able to do all you need as well with gFTP or proftpd.

Cheerio !

---

### Post by harerama on 2006-09-25
Hello,

I am using gftp and it's working just fine. Why don't you try it?
You can install it from System>Administration>Synaptic package manager.

Hope gFTP will work out.

---

### Post by dmizer on 2006-09-25
> **Varz said:**
> Is the only way to access FTP through a ftp client program?

nope.

you can do it through firefox: [ftp://server.com:port](ftp://server.com:port)

or ... you can click on places > connect to server ... choose ftp.  enter your server information and shezam, connected with no extra software to install.

edit:
forgot about command line:
```
ftp
ftp> open server port
Connected to server.
220 you're at home
Name (server:un): username
331 Password required for username.
Password:
230 welcome !!!
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-xr-x   2 (?)      (?)          4096 Sep 22 07:47 download
drwxrwxrwx   2 (?)      (?)          4096 Sep 25 02:35 upload
-rw-r--r--   1 (?)      (?)           166 Sep  5  2005 welcome.msg
226 Transfer complete.
ftp>
```

---

### Post by Varz on 2006-09-25
I did try gFTP before but for some reason it kept on crashing.

>  or ... you can click on places > connect to server ... choose ftp. enter your server information and shezam, connected with no extra software to install.[

That worked...but I would like to be able to connect using a webrowser.

When I had FTP running in windows with Filezilla it would ask for your username and password when you tried to connect in a webrowser, but for some reason vsftpd doesn't do that, it just thinks someone is trying to get anonymous access which I have denied.  

When I connect by doing what you said it must be sending the username and password all at once so I don't get that error message.  Maybe there's an option to enable a login window or something so it doesn't thinkn I'm trying to get anonymous access, I'll have a look.  Otherwise I'll have to use a ftp client or a batch file to get access in windows.

Thanks.

---

### Post by dmizer on 2006-09-25
don't know how this compares to filezilla as i never used it, but there's an ftp extension for linux firefox too:

fireftp.mozdev.org.  it works, i just tried it on my own ftp server, and it does allow anonymous login.

---

### Post by GJS on 2006-09-25
IE in Windows assumes that you are trying an annonymous connection then offers a username and password box if the connection is refused.  I expect that the response from your FTP server does not suit IE so you are not offered the option.  All you need to do in IE under Windows is type in the address of your FTP server in the URL bar then from the File menu select "Log in As..." and enter the details.  Check "save password" and uncheck "Log on Anonymously".

Remember that IE and any other browser that can make FTP connections is just acting as a FTP client, just often not a very good one.

'Hope that helps.

---

### Post by Varz on 2006-09-27
OK, so no-one knows a way to get the login screen to come up automatically using vsftpd then?

If so I'll just do what you said.

Thanks.

---

### Post by dmizer on 2006-09-27
vsftpd is an ftp server ...  not an ftp client.

are you trying to set up an ftp server, or do you just want to be able to log into ftp sites with firefox?  because if you just want to log into ftp sites with firefox, vsftpd is not gonna do it.

if you just want to log into an ftp site with firefox, type the site into the url bar like so:
[ftp://sitename.com](ftp://sitename.com)

then it will present you with your login prompt.

---

### Post by Varz on 2006-10-04
Ok I'm probably not explaining myself properly.

On Filezilla the program I used before I could set up an ftp server and log into the server via firefox by typing [ftp://(mydomainname)](ftp://(mydomainname)).  When I reached my site it would show a login window.

On vsftpd when I enter my domain name (like [ftp://(mydomainname)](ftp://(mydomainname)))  it just says it doesn't allow anonymous connections and it doesn't show a login window.

I was wondering if there was a way to enable a login prompt window with vsftpd when you reach the site so I can login.

I can login using other ftp clients because they have the option to send your username and password when connecting, but I would rather login through a webrowser.

---

### Post by dmizer on 2006-10-04
well, start by posting your vsftpd conf file.

it should have a line in it that says:
anonymous_enable=NO

if not, adding it might correct your problem.

---

