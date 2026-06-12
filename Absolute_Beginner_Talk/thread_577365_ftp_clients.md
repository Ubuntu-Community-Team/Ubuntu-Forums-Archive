---
title: "ftp clients?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-16
[SIZE="3"]I have just installed Ubuntu in a dual boot machine. I installed the Filezilla because I use in Windows, and it really works well in Windows. I tried the Filezilla for Linux, but it seems to time out without connecting, although it has all the same settings.

So I tried FireFTP. It's great virtue is that it keeps trying, but its great fault is that it does not connect. So I went to Add/Remove and looked for something there and found gFTP. Said it is supported by Canonical. I looked at it and did not know what to do or where to fill in information for my connection. 

No problem, I figure. I go to the Ubuntu support pages, Nothing in the official documentation that I could see about FTP. So I go to the community page and [***_[COLOR="RoyalBlue"]type in gFTP in the search[/COLOR]_***]("https://help.ubuntu.com/community/?action=fullsearch&context=180&value=gFTP&titlesearch=Titles") box. It says: *Title Search: "gFTP" 0 results of about 3111 pages. (0.06 seconds*. 

So I Googled [***_[COLOR="RoyalBlue"]gFTP Documentation[/COLOR]_***]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=47N&q=gftp+documentation&btnG=Search") which overwhelms me with sites but not any information of use to me. The [[COLOR="RoyalBlue"]***_official gFTP site_***[/COLOR]]("http://gftp.seul.org/") is completely uninformative for those wishing a how-to-use guide

Maybe someone can point me in the right direction. I'd appreciate that.[/SIZE]

---

### Post by mwiseley on 2007-10-16
Alan,

It's not always obvious, so I'll point this out... Nautilus, the file manager Ubuntu uses, has a great FTP client built right in.  To open up an FTP server, go to the Places menu in the top menu bar, and select "Connect to Server...". From there it's pretty obvious. This allows you to interact with FTP just like any other folder. 

What I like about this is it allows me to interact with file systems over different protocols in the same way, without having to use a different program for each.

Matt

---

### Post by Alan Stancliff on 2007-10-16
> **mwiseley said:**
> Alan,

It's not always obvious, so I'll point this out... Nautilus, the file manager Ubuntu uses, has a great FTP client built right in.  To open up an FTP server, go to the Places menu in the top menu bar, and select "Connect to Server...". From there it's pretty obvious. This allows you to interact with FTP just like any other folder. 

What I like about this is it allows me to interact with file systems over different protocols in the same way, without having to use a different program for each.

Matt
Thanks for pointing that out to me. It looks like it would be useful for public FTP sites. When I tried to access the site that has my web page, there was no place to enter a password. 

What I really need is something that will allow me to upload content to my web site, which you are invited to visit by clicking on the link below my name.

---

### Post by vikram on 2007-10-16
In Konqueror (KDE file manager/browser) you type 
[ftp://username:password@ftp.website.com](ftp://username:password@ftp.website.com)
or
[ftp://username@ftp.website.com](ftp://username@ftp.website.com) and the 
browser asks you for the password.

try this in Nautilus (Konqueror's GNOME equivalent).
they may be the same.

also see 
[http://osresources.com/3_19_en.html](http://osresources.com/3_19_en.html)

---

### Post by oldos2er on 2007-10-16
> **Alan Stancliff said:**
> Thanks for pointing that out to me. It looks like it would be useful for public FTP sites. When I tried to access the site that has my web page, there was no place to enter a password. 

What I really need is something that will allow me to upload content to my web site, which you are invited to visit by clicking on the link below my name.

 You need to change the 'Service Type' to FTP with login or whatever your website needs (ssh, etc.).

---

### Post by _teo_ on 2007-10-29
> **mwiseley said:**
> 
...
It's not always obvious, so I'll point this out... Nautilus, the file manager Ubuntu uses, has a great FTP client built right in.
...
Matt

Thanks for the tip. I've alway used the command-line utility, but this is nice to know.

---

