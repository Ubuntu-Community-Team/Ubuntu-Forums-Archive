---
title: "Ubuntu or Windows"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by reveiled on 2006-10-26
I have a file server home( music, Pic, docs +200GB)
For long it has been running on WinXP Pro.
Well today since i changed from DSL to Cable and am planning on cleaning my desk area. I also decided to restart the sever and freshen up.
SO my main question is Ubuntu or XP Pro
My setup: Imac intel, dell XP pro, HP media center
Sony vaio XP pro for server.
view pic :
[IMG]http://rvld.net/hosting/images/desk.png[/IMG]

---

### Post by halitech on 2006-10-26
personally I'd say ubuntu server with ftp and samba access and ssh and then you can have it sit in a corner headless and just forget about it. what type of hardware are you thinking or running it on?

---

### Post by seijuro on 2006-10-27
for starters ubuntu server is going to leave a smaller footprint than windows xp if you are just using it for a fileserve also it has the flexability to be more at the drop of a hat with minimal effort for example I like to use my server as a test bed for web applications before uploading them to their final destination to make sure all the bugs are worked out before giving access to the application to the public.

---

### Post by deadgobby on 2006-10-27
If you are thinking about using Ubie for music. Is it studio use or just ripping mp3's. If you are looking for music composing. There is Ubuntu Studio. This is one cool project.
[http://ubuntustudio.com/](http://ubuntustudio.com/)

---

### Post by IYY on 2006-10-27
This is an Ubuntu forum, so obviously we'll suggest Ubuntu. Some of the things you can't (as easily) do on a Windows server:

- When miles away from home, SSH to your machine and start a bittorrent download, or initiate a system upgrade.

- Easier installation/configuration time. This may sound surprising, but despite the fact that I have more years of Windows experience, I have a lot of trouble installing the official Microsoft FTP server on some versions of XP. 

- NFS sharing with the Mac. I am not actually sure about this one because I don't own a Mac, but I think it should be able to handle NFS sharing better (more reliable) than Windows-network sharing.

- I guess this doesn't matter in your case since the server is a laptop, but I always find the fact that there is no need for a monitor handy. All access to the server I just do remotely over SSH, even if it's physically located under my desk.

---

### Post by reveiled on 2006-10-27
Alright maybe that will help you a lot.
Here is my setup.
Sony VAIO (file Server)- P42.1ghz, 1GB RAM, 1TB
iMAC intel - ICD, 1GB RAM, 160GB HDD
Dell B130 - PM, 1GB RAM, 80GB HDD, XP Pro
HP Media Center - dont quite remember specs

I use my VAIO as server and it had Win XP Pro on it. With hamachi all my files were accesible worldwide.
My dell is my work computer and Picasa, iTunes are working fine with hamachi
My media center, well just there for the media center feature, matter fact i barly use it since i've been loving front row more and more.
my mac well this is my main computer at home.
Now i did installl ubuntu last night, just to try it. It was still downloading updates when i headed to sleep. I knew most people here would say go linux but i want to know, is it really worth it, running 3 OS.
How will ubuntu really benefit me, i dont know the shell thing, i use it just to extract and run files on my web server.
I have used a live disk for about a week(on my dell), and i think ubuntu is great but on my webserver, which i use to acces with RDC, is there still such a program? now what about FAT, NTFS, which format will linux, mac and pc all understand?
networking them, i am not sure hamachi works on linux, cant acces the site form work.
Please give me ur insights on that
and any info that you need that will help you guide me better just ask

---

### Post by IYY on 2006-10-27
> How will ubuntu really benefit me, i dont know the shell thing, i use it just to extract and run files on my web server.

You could always learn at least the basics of the shell. If you don't, there really isn't much benefit to Ubuntu other than stability and reliability.

> ow what about FAT, NTFS, which format will linux, mac and pc all understand?

FAT32 is understood by all, but it has some severe limitations (can't handle files that are too large). Linux can read NTFS, but not write to it.

---

### Post by reveiled on 2006-10-27
so if i cant write NTFS and cant read big files in fat( how big anyway ) 
so linux is not worth it i guess
i do a lot of torrent files, sometimes reaching up to 3GB a file and i recently got LOST 12GB
will it read/write those?
also my screen will only display 640*480 on my vaio
where do i get drivers?? SDM-M51D

---

