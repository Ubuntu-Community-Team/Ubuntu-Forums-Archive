---
title: "Help with wget"
date: 2014-06-25
forum: Any Other OS
---

### Post by Alypios on 2014-06-25
I'm sorry if this is not the right place to make this thread, I have gotten tired of trying to search for this and not even knowing where to start, plus I figured I would go to a forum revolving around linux seeing as this is a linux command. Anyway, I recently started on this endeavor in Windows to create a batch file that will go to certain webpages and download files that I use on a daily basis at work such as Combofix, tdsskiller, ect... I ran into an issue using Windows command line while downloading tdsskiller where it would "download" but not have actually grabbed the .exe and I talked with my boss and he said to install Cygwin with the wget command installed. After a little while I had gotten the hang of it and had several programs downloading through cmd using wget. My issue is there are several programs that I want to update on a regular basis but can't because the names change with each update, programs like adwcleaner which is now named adwcleaner_3.312.exe. Now if you go to the website ( [https://toolslib.net/downloads/finish/1/](https://toolslib.net/downloads/finish/1/) ) after a few seconds it will have a pop up menu that you can save said program. I want to know if it possible to tell the command wait for the popup and download the file, and also ignore the name. I've been looking in to this for about a week and the closest thing I can find is```
wget -r -l1 -H -t1 -nd -N -np -A.mp3 -erobots=off -i ~/mp3blogs.txt
```with the command -A.mp3 looking for .mp3 files in various levels of the website. Any suggestions?

---

### Post by oldos2er on 2014-06-25
Moved to Other OS/Distro Support.

---

### Post by Alypios on 2014-07-01
Let me add some more information just in case people do not understand. I'm using wget to download .exe files through cygwin attached to command prompt. The code I'm using for example is```
wget -N [http://media.kaspersky.com/utilities/VirusUtilities/EN/tdsskiller.exe](http://media.kaspersky.com/utilities/VirusUtilities/EN/tdsskiller.exe)
```. Works like a charm, but if I were to try downloading adwcleaner from their website I would like to use```
 wget -N [https://toolslib.net/downloads/finish/1/adwcleaner.exe](https://toolslib.net/downloads/finish/1/adwcleaner.exe)
```, vs ```
wget -N [https://toolslib.net/downloads/finish/1/awdcleaner_3.214.exe](https://toolslib.net/downloads/finish/1/awdcleaner_3.214.exe)
```. I don't know how or if it is possible to make wget ignore the name, if I use the later, then this batch file I created would have to be updated after each release. Which then I would just go download it instead of using wget for that file.

---

### Post by ian-weisser on 2014-07-01
wget is a great little downloader. It's not a web page parser.

From your description, you seem to need to parse the web page or the javascript...whatever is generating the link you are looking for. You can do that parsing using shell script, or perl, or Python, or a dozen other languages. Once you have the link, then you can download it. If your parsing script is in shell code, then wget would be appropriate.

---

### Post by coldraven on 2014-07-02
Is this any help? 
[http://www.perl.com/pub/2003/01/22/mechanize.html](http://www.perl.com/pub/2003/01/22/mechanize.html)


Examples:
[http://search.cpan.org/~jesse/WWW-Mechanize-1.72/lib/WWW/Mechanize.pm](http://search.cpan.org/~jesse/WWW-Mechanize-1.72/lib/WWW/Mechanize.pm)

---

### Post by Alypios on 2014-07-02
Thank you guys so much. I'll begin looking into your suggestions tonight.

---

