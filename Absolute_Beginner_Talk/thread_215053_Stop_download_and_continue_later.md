---
title: "Stop download and continue later?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-13
Since Im downloading a 3gb file as it is now, is there any way, I can stop it, and then return to download it later?

---

### Post by Kobalt on 2006-07-13
For such big files you should (if you can) use a torrent... This way you could stop and start again later your download easily. I don't know a way to catch up a "regular" download actually.

---

### Post by Sonic Alpha on 2006-07-13
In Windows you have the likes of GetRight, FlashGet, and Free Download Manager.

I saw something called "[Downloader for X]("http://www.krasu.ru/soft/chuchelo/")", though I don't know if it's complete yet (the site is a little broken) :/

**Update:** Managed to find a [list of downloadable files]("http://www.krasu.ru/soft/chuchelo/files/") from the site

---

### Post by Ragazzo on 2006-07-13
The program you're looking for is called a download manager. Here's one from the Ubuntu Guide: [Download Manager]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Download_Manager_.28Downloader_for_X.29")

---

### Post by aysiu on 2006-07-13
```
wget -c http://www.sitename.com/verylargefile.extension
```

I believe the *wget* command has a *-c* that allows you to continue downloading a partially downloaded file: ```
       -c
       --continue
           Continue getting a partially-downloaded file.  This is useful when
           you want to finish up a download started by a previous instance of
           Wget, or by another program.  For instance:

                   wget -c ftp://sunsite.doc.ic.ac.uk/ls-lR.Z

           If there is a file named ls-lR.Z in the current directory, Wget
           will assume that it is the first portion of the remote file, and
           will ask the server to continue the retrieval from an offset equal
           to the length of the local file.

           Note that you don&#8217;t need to specify this option if you just want
           the current invocation of Wget to retry downloading a file should
           the connection be lost midway through.  This is the default behav&#8208;
           ior.  -c only affects resumption of downloads started prior to this
           invocation of Wget, and whose local files are still sitting around.

           Without -c, the previous example would just download the remote
           file to ls-lR.Z.1, leaving the truncated ls-lR.Z file alone.

           Beginning with Wget 1.7, if you use -c on a non-empty file, and it
           turns out that the server does not support continued downloading,
           Wget will refuse to start the download from scratch, which would
           effectively ruin existing contents.  If you really want the down&#8208;
           load to start from scratch, remove the file.

           Also beginning with Wget 1.7, if you use -c on a file which is of
           equal size as the one on the server, Wget will refuse to download
           the file and print an explanatory message.  The same happens when
           the file is smaller on the server than locally (presumably because
           it was changed on the server since your last download
           attempt)---because &#8216;&#8216;continuing&#8217;&#8217; is not meaningful, no download
           occurs.

           On the other side of the coin, while using -c, any file that&#8217;s big&#8208;
           ger on the server than locally will be considered an incomplete
           download and only "(length(remote) - length(local))" bytes will be
           downloaded and tacked onto the end of the local file.  This behav&#8208;
           ior can be desirable in certain cases---for instance, you can use
           wget -c to download just the new portion that&#8217;s been appended to a
           data collection or log file.

           However, if the file is bigger on the server because it&#8217;s been
           changed, as opposed to just appended to, you&#8217;ll end up with a gar&#8208;
           bled file.  Wget has no way of verifying that the local file is
           really a valid prefix of the remote file.  You need to be espe&#8208;
           cially careful of this when using -c in conjunction with -r, since
           every file will be considered as an "incomplete download" candi&#8208;
           date.

           Another instance where you&#8217;ll get a garbled file if you try to use
           -c is if you have a lame HTTP proxy that inserts a &#8216;&#8216;transfer
 interrupted&#8217;&#8217; string into the local file.  In the future a &#8216;&#8216;roll&#8208;
           back&#8217;&#8217; option may be added to deal with this case.

           Note that -c only works with FTP servers and with HTTP servers that
           support the "Range" header.
```

---

### Post by elettronicha on 2006-07-13
Or simply try using the command wget; from the directory you want the file to be downloaded to:

wget -c [http://path/to/the/file](http://path/to/the/file)

From man wget:
> -c
       --continue
           Continue getting a partially-downloaded file.  This is useful when
           you want to finish up a download started by a previous instance of
           Wget, or by another program.  For instance:

                   wget -c [ftp://sunsite.doc.ic.ac.uk/ls-lR.Z](ftp://sunsite.doc.ic.ac.uk/ls-lR.Z)

           If there is a file named ls-lR.Z in the current directory, Wget
           will assume that it is the first portion of the remote file, and
           will ask the server to continue the retrieval from an offset equal
           to the length of the local file.

;)

PS: sorry, I posted while aysiu was posting, so didn't note his answer.

---

### Post by Ragazzo on 2006-07-13
There is also gwget which gives you a nice GUI to wget if you don't want to use command line.

---

### Post by aysiu on 2006-07-13
From [the *gwget* website](http://www.gnome.org/projects/gwget/index.html): > **Resume:** By default, gwget tries to continue any download.

---

### Post by AndrewCaul on 2006-07-13
wget has become an essential tool in my daily Internetting. When you use dial-up like I do, you need something better than Firefox for downloading 50 MB audio files. :) 
I even ended up downloading the Windows version of wget for those rare times when I'm using Windows to surf the Internets.

---

### Post by aysiu on 2006-07-13
My wife got frustrated at one point because she wanted to download an entire website and didn't know how to do it. So I showed her the *wget* command--solved her problem with one command and just a matter of seconds: ```
wget -c -r http://www.sitename.com
``` *wget* is a very powerful tool.

---

### Post by bailout on 2006-07-13
Get a decent browser ie Opera;) It has a built in dl manager that allows pause and restart

---

### Post by wildseven on 2006-07-13
> **Ragazzo said:**
> There is also gwget which gives you a nice GUI to wget if you don't want to use command line.

but the terminal is why it's fun :)

---

### Post by Ragazzo on 2006-07-13
> **wildseven said:**
> but the terminal is why it's fun :)

For some people the terminal is why it isn't fun :)

---

### Post by elettronicha on 2006-07-13
I think in this case working with the command line it's easier than using a graphical tool. Just open a terminal and type 'wget -c blablabla' and that's it, whithout having installed a thing.:)

---

### Post by AndrewCaul on 2006-07-18
> **elettronicha said:**
> I think in this case working with the command line it's easier than using a graphical tool. Just open a terminal and type 'wget -c blablabla' and that's it, whithout having installed a thing.:)

And the command line keeps a command history, which makes continuing downloads too easy.

---

### Post by gThree on 2006-07-18
For Firefox:

[DownThemAll]("https://addons.mozilla.org/firefox/201/")

---

### Post by cbudden on 2006-07-18
As someone already said, Downloader for X, 
```

sudo apt-get install d4x

```

---

