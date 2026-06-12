---
title: "How to File share/webserve?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-29
Not sure under what category this would fall...

A feature in Win Home Server is that it can setup a webpage, to allow certain users, access its shared directories.  This can allow the user to view photos and even download files.

Due to the Home Server problems, I chose to go with Ubuntu... and I haven't looked back.

While the above was lower on the priorty list, I've gotten most of my high priorties met.

Can anyone point me in the direction on how to what I've explained above?  This would include any security precautions that need to be addressed...

Thanks!

---

### Post by Dr Small on 2008-03-29
Basically, you want a webserver?
That can be easily setup with Xampp:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

Dr Small

---

### Post by BlizzofOZ on 2008-03-29
> **Dr Small said:**
> Basically, you want a webserver?
That can be easily setup with Xampp:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

Dr Small

Thanks Dr Small... I appreciate your quick reply.

I'll look into your guide... but the more I think about this (and excuse my web-noobisity), I might be more wanting FTP than a webserver.  What is the difference?

I'm thinking webserver will give my pretty pages and such, where I can view photos online, etc. 

While FTP will just show a directory structure where I can basically do file uploads/downloads.  Correct?

Is there a difference in security?  Is one "better" than the other? I'm sure it just depends on my needs... At the moment, I want to be able to share files with particular people, over the internet.

---

### Post by Dr Small on 2008-03-29
Xampp is a webserver that runs apache, the webserver that powers most of the internet. FTP is a File Transfer Protocol that is insecure and was generally used to upload and download files.

Xampp is far more secure than FTP, and you can make whatever you want on the webserver, which also has Php on it for web development.

Dr Small

---

### Post by Nythain on 2008-03-29
if the webserver is set up right, and url doesnt actually contain an html or other form of web page, it should actually just display the directory contents and allow visitors to view or download whatever files... at least most web servers do... though it is/can be quite the security risk, so the more popular webservers will actually display "default" page if there's no index.* file already in existance... but if you are just wanting other users to be able to download files, then ftp would probably be the better of the ideas/options

---

