---
title: "Is there a program that downloads files in order?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by dnns123 on 2007-10-14
I like reading Japanese comics, or manga, but I'd like it better if I can read it straight away without downloading/viewing the pictures one by one. Sites usually have no packages. So, is there a program that can download the pictures by order? For example:

[www.onemanga.com/1/2/1.jpg](www.onemanga.com/1/2/1.jpg)
[www.onemanga.com/1/2/2.jpg](www.onemanga.com/1/2/2.jpg)
[www.onemanga.com/1/2/3.jpg](www.onemanga.com/1/2/3.jpg)
[www.onemanga.com/1/2/4.jpg](www.onemanga.com/1/2/4.jpg)

I'd like a program that can download the files like, 
Download from: [http://www.onemanga.com/1/2/#.jpg](http://www.onemanga.com/1/2/#.jpg)
then another box that has "1" to "4"


So, is there a program that can download the pictures by order, or something like that?

---

### Post by juantovarm on 2007-10-14
Hey i am currently reading Bleach, what i do is download the whole manga and read it with Comix. The link you posted gave me the One MAnga home page. The mangas i checked, Blame 40 and Hatsukoi limited, are only available to read online. No package to download. It is a lot easier if you find a zip file. Just download it and open it with comix that is available in add/remove programs. 

Hope it helps
Juan

---

### Post by dnns123 on 2007-10-14
Comix really doesnt answer the question, I can read images with the image viewer, but the hassle of downloading a chapter of pages one by one is tiring. My objective is to download the 170++ chapters of Air Gear

---

### Post by juantovarm on 2007-10-14
you then might want to try a firefox addon called scrapbook, it downloads the web page completely and all internal links, pretty much like spiderzilla which is only for windows

hope it helps

---

### Post by HermanAB on 2007-10-14
wget?

---

### Post by avik on 2007-10-15
wget should work.  According to the man(ual) page for wget, the command you're looking for is:

```

wget -r -l1 --no-parent -A.jpg http://www.onemanga.com/1/2/

```

---

### Post by hyper_ch on 2007-10-15
Well, you cuold also use httrack. It's a program that lets you download a full webpage and subfolders and such. Many options to set so that only images are fetched (for example).

You can store it as project also and run it later again, then only the new stuff will be downloaded. Not 100% sure if that is what you are looking for.

(I used it to download 19k+ Wallpapers ;) )

---

### Post by TaTooKax on 2008-02-04
well , I created a not-so-long bash script that downloads every page in a Manga chapter just from onemanga.com.

You can see the post in my blog, although it's in spanish... [[COLOR="Red"]here[/COLOR]]("http://tatooka.wordpress.com/2008/02/04/descargando-manga-a-lo-hacker/")

or you can get the bash script directly from [[COLOR="Red"]here[/COLOR]]("http://www.driveway.com/k0o5r8l6u3")

Usage is:

```
./download_manga.sh [image_server_id] [manga_id] [chapter_id]
```

where, in the URL:

```
http://img[IMAGE_SERVER_ID].onemanga.com/mangas/[MANGA_ID]/[CHAPTER_ID]/[PAGE_NUMBER].jpg
```

so basically all you have to do is get into onemanga.com, choose a Manga, check what image_server it uses, check the manga_id and then run the script with that data. For example...

```
/download_manga.sh 16 150 01
```

...would download every page in the chapter 01 from the manga 150 in the image server "img16".

Also, the script already creates a RAR from the downloaded JPGs and then renames it to CBR, ready to use with Comix :)

good luck!

---

