---
title: "How to update firefox to 2.0?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-30
hey (again! im a reall n00b lol)

Currently have firefox 1.5.0.7 installed on this computer runing ubuntu dapper.

Iv looked through synaptic, and all the firefox vershions seem to be the one i have, and i tried sudo apt-get update firefox, and sudo apt-get install firefox which told me that i already had it.

I know 2.0 is out, as i have it on my windows machien. but how do i get it on ubuntu?  I really need the built in spell checker 2.0 has! lol (im dyslexic)

thanks :)

---

### Post by xyz on 2006-10-30
[ Here is a nice place to go to...]("https://help.ubuntu.com/community/FirefoxNewVersion")
Good day!

---

### Post by Tobywuk on 2006-10-30
thanks. On that page there is a link called "automated install of firefox" it downloaded a script with the name installnewfirefox.sh   

How do i run a script?

---

### Post by caravel on 2006-10-30
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by dmizer on 2006-10-30
here is a more complete tutorial: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Tobywuk on 2006-10-30
Thank you. I'v now run the script and installed it.

2 questions.

1. What permission is being set on the file in "chmod +x installnewfirefox.sh"?

and 2. Now its installed, i cant see it on my applications menue. How do i run the application, and put it on the applications menue?

Thanks :)

---

### Post by dmizer on 2006-10-30
1) you are setting the permission of the script to be executable by you.

2) click on the same thing you were clicking on before to open firefox.  it will now open the new firefox instead of the old.

---

### Post by xyz on 2006-10-30
> **dmizer said:**
> here is a more complete tutorial: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
I wanted to try that way (Method # 3), too but I didn't quite understand the following:
> Enter your choice of localization:
I mean does the place where I live matter at all? I want "en", though.
Thanks for clearing this up for me.

---

### Post by Zdravko on 2006-10-30
> **Tobywuk said:**
> 
I know 2.0 is out, as i have it on my windows machien. but how do i get it on ubuntu? I really need the built in spell checker 2.0 has! lol (im dyslexic)
 
thanks :)
I don't think that only because of this feature you will want to trick the system and install manually FF. I suggest you to wait some time (5-6 weeks). when Ubuntu will accept the new FF version.

---

### Post by Tobywuk on 2006-10-30
when i click the internet icon, like i normaly do to load up firefox, it still loads up the old vershion and not 2.0

Maby i need to do a restart or something?

---

### Post by SunnyRabbiera on 2006-10-30
Me I just do it the normal way, download the tar, extract and put the firefox folder where I know where it would be (like the home folder) and make a link to it on my desktop.
Anyhow most programs are going to be installed in /usr/bin, but I am not sure as this can vary per installation method.

---

### Post by dmizer on 2006-10-30
if you just want a spell checker, you can install the aspellfox extension.  it gives you a right click on-demand spell checker in any version of firefox you may have installed.

---

### Post by dmizer on 2006-10-30
> **xyz said:**
> I wanted to try that way (Method # 3), too but I didn't quite understand the following:

I mean does the place where I live matter at all? I want "en", though.
Thanks for clearing this up for me.
you should enter your locale here, that is ... your system language.  eg: en_GB

to figure out what your system is set up to use, simply type -> [COLOR="Red"]locale[/COLOR] in the terminal and it will tell you what you're set up to use.

> **Tobywuk said:**
> when i click the internet icon, like i normaly do to load up firefox, it still loads up the old vershion and not 2.0

Maby i need to do a restart or something?

which method mentioned in this thread did you end up using to install firefox 2.0?

---

### Post by Tobywuk on 2006-10-30
i used the firefoxinstall.sh  file, and run it in the terminal

---

### Post by starkmann on 2006-11-04
This was mentioned a few posts ago in this thread but I tried updating to firefox 2.0 today and did some searching on google and found all the links you listed about. I got :
> Enter your choice of localization:
 at the end of the script recommended above.I tried some different answers and got that it needed to a be a numeric answer. I experimented with 1 and 2 which seem to relate to, possibly the site where I am pulling the files from (maybe??) No matter which I picked, I always got a message that it failed at the end. I can provide further details if needed. Any help is appreciated. Naturally I will keep playing with this in the mean time.

So I sorted it out. I needed to read teh list higher up in the script that. It had numbers and text off to the right. At first the text didn['t seem to mean anything but it was the download site apparently. I had already downloaded it but did it this way anyway because I had a script. I had to find en-us (number 11 as I recall) and type that in. I'm not sure what the first 9 or 10 sites were all about but once I found the english ones it worked fine.

---

### Post by elcasey on 2006-11-04
I installed Firefox 2.0 for Dapper using [this script I found](http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/) on Wordpress *but* I forgot to edit the script to "en-US" from "en-GB" before I ran it.

Having said that, if I edit the script and re-run it is it going to break my plugins, bookmarks, extensions, etc? I've got everything working nicely now from DVDs to .mp4s to Java and Flash and I want to keep it that way. 

But I also want to see it spelled "customize" and "disk" and not "customise" and "disc." Just me being a regionalist, I guess. :mrgreen:

---

### Post by visvak on 2006-11-11
go ahead and edit the script and run it again. i assure you, all your plugins, bookmarks, extensions and whatever else will be fine.

---

### Post by elcasey on 2006-11-15
I didn't see this answer until after I did it, but I decided to edit the script and run it again and nothing broke... so, for anyone else who forgot to edit that script to your locale, you can change it at your leisure (pronounced "lezh-ur" if you installed the en-GB version :p ).

Other than Wine, I've got everything else working marvelously!

---

