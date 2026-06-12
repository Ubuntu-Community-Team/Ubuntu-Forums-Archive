---
title: "Online Storage Options"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by magwhyte on 2007-11-24
Does anyone know of an Ubuntu friendly online storage options (i.e. xdrive.com, etc.).  Most of the software for uploading files is exclusively Windows, but a few offering Mac options.

I noticed that Jungle Disk offered a Linux option, but (IMHO) it is terrible.  It installed, now I can't find it.  Oh well...

Any insights, anyone?

Adrian

---

### Post by mahiyar on 2007-11-25
If it is not tons of data, I use gmail.

---

### Post by Xavieran on 2007-11-25
Try [mediafire]("www.mediafire.com") i find their interface very good and you can password protect certain items.

---

### Post by magwhyte on 2007-11-25
Thanks for the replies.  They were really helpful.  I decided to go with Mediafire.  It's just so simple and elegant.  Plus couldn't resist the price (or current lack thereof).

Many thanks...

Adrian
:)

---

### Post by mahiyar on 2007-11-25
I too visited the mediafire site seems to be good.

---

### Post by moktor on 2008-01-07
Thanks for the mediafire recommendation! I'm definitely going to check it out. I was looking for an online storage option as well to backup some documents and pictures, but just about everything required windows. If I am going to pay for an online storage option I would prefer that it at least

Right now I'm using the GSpace extension for Firefox to store stuff in Gmail, which works really well, but I'm not certain it is in line with the EULA/TOS.

---

### Post by hyper_ch on 2008-01-07
is this sensitive data?

---

### Post by kleo skywalker on 2008-01-07
I use Google's stuff - like Docs and Spreadsheets. I haven't tried Picassa in Ubuntu, but when I had Windows I just used to email whole albums at once to my Gmail account.

---

### Post by moktor on 2008-01-08
> **hyper_ch said:**
> is this sensitive data?

Most of the stuff I'm looking to backup isn't really sensitive. Mostly just various papers, some source code from old projects, and quite a few full-resolutions versions of photographs. Not necessarily stuff I couldn't live without, but just various things that it would give me peace of mind to know is safely stored off-site somewhere. If I do run across anything sensitive I'll probably encrypt it with GnuPG.

---

### Post by sgleo87 on 2008-01-13
I am also in the same boat...looking for an online storage site that is secure (includes some sensitive data like account numbers and passwords). I have heard about spideroak and jungledisk but have not tried them yet so I don't know how they would compare to mediafire. 

What I am looking for:
- secure storage
- automatic incremental backup (otherwise I'll forget to do it regularly)
- free or low cost

Any recommendations?

---

### Post by hyper_ch on 2008-01-14
Well, there are quite a few "webhosts" that offer a nice amount of diskspace and shell access for a very low rate.

So if it is not sensitive data and you just need a remote backup location, then you could maybe use one of those. with rsync you can easily backup there.

---

### Post by tmtjjhnsn on 2008-01-20
I am using Jungle Disk, and I find it to be easy, automatic, and inexpensive.  Also, the data is encrypted on the user's local machine, so that it is not readable to anyone with access to Amazon's servers.  Amazon does not know or ask for the user's encryption key.

After downloading the tar file from the Jungle Disk website to my desktop, I double clicked on it, which launched the archive manager.  I then clicked Extract.  One of the extracted files was called junglediskmonitor, which I dragged to the panel at the top of the desktop, creating a launcher that starts the Jungle Disk Monitor anytime I click on it.  Personally, I leave Jungle Disk Monitor running at all times, and I have it configured it to backup my files automatically.  The monitor puts an icon in the Gnome panel when running.  Clicking on the icon, then on Help, then on Connecting to your Jungle Disk...  takes you to instructions on how to see your backed up files as though they were on a local disk on your machine.  

I think it's cool.

---

### Post by 0x656b694d on 2008-06-08
Hi,

Try the [who.hasfiles.com]("http://who.hasfiles.com") service.
It can be accessible via webdav protocol so you may mount the storage.
You may also upload files via simple web interface and share files between registered friends.
100 MiB for free. More space and secure connection costs some.

Regards,
-Mike.

---

### Post by hyper_ch on 2008-06-09
you can use gmail also... there are tools that allow you to access it like a ftp account. Then yuo can use duplicity (maybe even with ftplicity) to created encrypted backups.

---

