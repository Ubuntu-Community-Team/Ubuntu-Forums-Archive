---
title: "Lightweight Linux distro with tesseract 3"
date: 2012-11-05
forum: Any Other OS
---

### Post by Kevin McCready on 2012-11-05
I am still new to Linux and have never built, compiled or made a package and have little idea what these things mean.

However, the distro I am on (Lubuntu) does not have tesseract 3. When I went to the google page to learn how to compile it etc, the instructions were appalling and aimed at people who had done this sort of thing before.

So I am thinking I would perhaps like to try a linux distro which has tesseract 3 available without having to learn to program these things.

Any help would be appreciated.

---

### Post by mips on 2012-11-05
There's a repo for it here [http://notesalexp.net/](http://notesalexp.net/)
or you could do [http://www.webupd8.org/2011/03/gimagereader-tesseract-ocr-gui-gets.html](http://www.webupd8.org/2011/03/gimagereader-tesseract-ocr-gui-gets.html)

Why do people always complicate things?

---

### Post by Kevin McCready on 2012-11-05
Thanks

Your first link I udnerstood until I got to the part which said:

*wget -O - **[http://notesalexp.net/debian/alexp_key.asc](http://notesalexp.net/debian/alexp_key.asc)*[I] 	| apt-key add

[/I]I am on Lubuntu which I think is Oneiric, so will the key work?

then what will happen when I type:
[I]
apt-get install package[/I]

what does "package" mean here?

Do I really have to do it as su? The google site also mentioned installing as a user.

Your second link ended up taking me to 
[http://sourceforge.net/projects/gimagereader/files/0.9/](http://sourceforge.net/projects/gimagereader/files/0.9/)
where I would still have to extract and play with a .gz file. I have no experience doing this.

Thanks again. Looking forward to your help again!

---

### Post by mips on 2012-11-05
> I am on Lubuntu which I think is Oneiric, so will the key work?

It's just a security/authenticity key for the repo.

> apt-get install package

what does "package" mean here?

The name of the *package* you want to install as per the list of packages available further down. "tesseract-ocr" is the package you are after. You will have to install it with **sudo apt-get install tesseract-ocr** or you can install it via the software centre or synaptic package manager once you have added the repo.

I don't know which version of ubuntu you have installed, you will have to tell us that 11.10, 12.04, 12.10 etc etc.

---

### Post by mips on 2012-11-05
> **Kevin McCready said:**
> 
Your second link ended up taking me to 
[http://sourceforge.net/projects/gimagereader/files/0.9/](http://sourceforge.net/projects/gimagereader/files/0.9/)
**where I would still have to extract and play with a .gz file.** I have no experience doing this.


No. There is a .deb file which is the native package format of ubuntu or debian. Download gimagereader_0.9-1_all.deb and simply install it.

You can install it via the software centre if you double click on the package or you can install it from the command line with **sudo dpkg -i gimagereader_0.9-1_all.deb**

---

### Post by Kevin McCready on 2012-11-05
I decided to try the second link as you suggested because it seemed easier.

I downloaded the .deb file as suggested. First I just clicked on the download and it installed. But when I tried to launch it from the menu nothing happened. So I reinstalled it again, this time with the dpkg command from the terminal as you suggested. I tried again to launch the program from the menu system but nothing happened. So I tried from the terminal by typing the command gimagereader and got the message:

Failed to load gImageReader modules, check your installation: No module named Image

---

### Post by mips on 2012-11-05
As far as i'm aware gimagereader is just a gui for tesseract and requires it to be installed so see step one.

---

### Post by Kevin McCready on 2012-11-05
I'm not sure which step one you mean?

But I tried the link you suggested:
[http://notesalexp.net/](http://notesalexp.net/)

I changed the sources.list file. Then when trying to get the key I got this error:

root@k-Presario-CQ57-Notebook-PC:~# wget -O - [http://notesalexp.net/debian/alexp_key.asc](http://notesalexp.net/debian/alexp_key.asc) | apt-key add
--2012-11-06 02:06:59--  [http://notesalexp.net/debian/alexp_key.asc](http://notesalexp.net/debian/alexp_key.asc)
Resolving notesalexp.net... gpg: can't open `': No such file or directory
82.146.39.165
Connecting to notesalexp.net|82.146.39.165|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10039 (9.8K) [application/pgp-signature]
Saving to: `STDOUT'

 0% [                                       ] 0           --.-K/s   in 0s      


Cannot write to `-' (Broken pipe).

---

### Post by Kevin McCready on 2012-11-05
I did some googling and what worked was this command with single commas and >>

wget -O - 'http://notesalexp.net/debian/alexp_key.asc' >> key.gpg
apt-key add key.gpg 

But when I tried to run tesseract from the terminal (I've given up on gImageReader for now) I got this error:

Error opening data file /usr/share/tesseract-ocr/tessdata/eng.traineddata
Please make sure the TESSDATA_PREFIX environment variable is set to the parent directory of your "tessdata" directory.
Failed loading language 'eng'
Tesseract couldn't load any languages!
Could not initialize tesseract.

---

### Post by snowpine on 2012-11-05
Tesseract 3 can be installed with a couple of clicks in the Software Center if you are using 12.04 or newer.

---

### Post by Kevin McCready on 2012-11-06
Thanks for that. I might just upgrade afterall.

---

