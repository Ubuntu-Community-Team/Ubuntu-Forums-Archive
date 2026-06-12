---
title: "Conky wont start"
date: 2014-08-25
forum: Any Other OS
---

### Post by firas2 on 2014-08-25
[http://u.cubeupload.com/elfc/snapshot4.png](http://u.cubeupload.com/elfc/snapshot4.png)

[I] would also Like to say    Because every time i ran conky I got this Little black box conky 

so I deleted the     
[/I]etc/conky/conky.conf   only the /conky.conf

[http://u.cubeupload.com/elfc/snapshot1.png](http://u.cubeupload.com/elfc/snapshot1.png)

[URL="http://u.cubeupload.com/elfc/snapshot3.png"]http://u.cubeupload.com/elfc/snapshot3.png

can any one help ? thank u 
[/URL]

---

### Post by deadflowr on 2014-08-25
I'm guessing you have a conky file in you home folder called .conkyrc1?
If so, either rename it simply ".conkyrc", or use the -c option
```
conky -c ~/.conkyrc1
```
do not run as root (sudo -i)

Tell us what happens next.

---

### Post by firas2 on 2014-08-25
Ok I remove  and uninstalled all conky folders and files     then i did a fresh install from   (synaptic package manager)

and this is where the files are 

 [http://u.cubeupload.com/elfc/REMOVECONKY1.png](http://u.cubeupload.com/elfc/REMOVECONKY1.png)

[http://u.cubeupload.com/elfc/pic1.png](http://u.cubeupload.com/elfc/pic1.png)


now where do I start with this fresh install please ???


UPDATE

ok so I found the original script   what do i do find me any script   and   copy and past there ??

---

### Post by firas2 on 2014-08-25
I get this  when i run the command 

[http://u.cubeupload.com/elfc/olp1.png](http://u.cubeupload.com/elfc/olp1.png)

---

### Post by Frogs Hair on 2014-08-25
That is the default conky configuration . Can you provide a link to the Conky configuration you are trying to use ?

---

### Post by coffeecat on 2014-08-25
*Thread moved to **Other Operating Systems and Projects**.*

You are running Linux Mint.

---

### Post by firas2 on 2014-08-25
> **Frogs Hair said:**
> That is the default conky configuration . Can you provide a link to the Conky configuration you are trying to use ?
dont have one now  because i deleted it 




> **coffeecat said:**
> *Thread moved to **Other Operating Systems and Projects**.*

You are running Linux Mint.
yes

---

### Post by deadflowr on 2014-08-25
> **Frogs Hair said:**
> That is the default conky configuration . Can you provide a link to the Conky configuration you are trying to use ?
+1
Do you have a file called .conkyrc1, or whatever it's called, inside your home folder?
In the terminal run
```
locate conky
```
see if any are listed in the home folder.
if so, maybe 
```
cat <the-filename-here>
```
and then copy and paste the output into a post in this thread
[Use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

Edit: forget most of the above, since it seems you no longer have any file anymore.
Do you remember where you got that file from?
Can you re-download it, or maybe another one?

---

### Post by vasa1 on 2014-08-25
> **Frogs Hair said:**
> That is the default conky configuration . Can you provide a link to the Conky configuration you are trying to use ?
You could look at this thread which seems more detailed: [http://forums.linuxmint.com/viewtopic.php?f=90&t=176199](http://forums.linuxmint.com/viewtopic.php?f=90&t=176199)

---

### Post by firas2 on 2014-08-25
As Requested  from an other member    
     [**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1276577")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]




```
bfk@bfk-D900C:~ > locate conky

/etc/conky
/etc/conky/conky.conf
/etc/conky/conky_no_x11.conf
/home/bfk/.conky
/home/bfk/.conkyrcy1
/home/bfk/.conkyrcy2
/home/bfk/.conkyrcy3
/home/bfk/conky___geek_inside_by_fenouille84-d3ae83i
/home/bfk/.conky/.conkyrcy1
/home/bfk/.conky/.conkyrcy2
/home/bfk/.conky/.conkyrcy3
/home/bfk/.conky/.directory
/home/bfk/.conky/Fêtes
/home/bfk/.conky/conkyrc1
/home/bfk/.conky/conkyrc2
/home/bfk/.conky/conkyterm
/home/bfk/.kde/share/apps/RecentDocuments/.conkyrcy1.desktop
/home/bfk/.kde/share/apps/RecentDocuments/.conkyrcy1[2].desktop
/home/bfk/.kde/share/apps/RecentDocuments/.conkyrcy2.desktop
/home/bfk/.linuxmint/mintUpload/services/conky
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_cal
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_clock
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_gmail
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_mpd
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_rss
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_speed
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_stod
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_tor
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conkyrc
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Clear.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Fair.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Light.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Mist.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Mostly.jpg
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Mostly.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Partly.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Rain.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/Sunny.png
/home/bfk/.local/share/Trash/files/haxOS_Conky/.conky_weather_icons/T-Storm.png
/home/bfk/conky___geek_inside_by_fenouille84-d3ae83i/Fêtes
/home/bfk/conky___geek_inside_by_fenouille84-d3ae83i/conkyrc1
/home/bfk/conky___geek_inside_by_fenouille84-d3ae83i/conkyrc2
/home/bfk/conky___geek_inside_by_fenouille84-d3ae83i/conkyterm
/usr/bin/conky
/usr/lib/conky
/usr/lib/conky/libcairo.so
/usr/lib/conky/libcairo.so.0.0.0
/usr/lib/conky/libimlib2.so
/usr/lib/conky/libimlib2.so.0.0.0
/usr/share/apport/package-hooks/conky.py
/usr/share/doc/conky
/usr/share/doc/conky-all
/usr/share/doc/conky-all/AUTHORS.gz
/usr/share/doc/conky-all/README.gz
/usr/share/doc/conky-all/TODO
/usr/share/doc/conky-all/changelog.Debian.gz
/usr/share/doc/conky-all/config_settings.html
/usr/share/doc/conky-all/copyright
/usr/share/doc/conky-all/docs.html
/usr/share/doc/conky-all/lua.html
/usr/share/doc/conky-all/variables.html
/usr/share/doc-base/conky-manual
/usr/share/man/man1/conky.1.gz
/usr/share/menu/conky-all
/var/cache/apt/archives/conky-all_1.9.0-4_amd64.deb
/var/cache/apt/archives/conky_1.9.0-4_all.deb
/var/lib/dpkg/info/conky-all.conffiles
/var/lib/dpkg/info/conky-all.list
/var/lib/dpkg/info/conky-all.md5sums
/var/lib/dpkg/info/conky-all.postinst
/var/lib/dpkg/info/conky-all.postrm
/var/lib/dpkg/info/conky.list
/var/lib/dpkg/info/conky.md5sums
```






this is the conky that I am trying to use    it has 3  files   left  center  right    conkyrc1   conkyrc2   conkyrc3

[http://u.cubeupload.com/elfc/capturedcran2.png](http://u.cubeupload.com/elfc/capturedcran2.png)

---

### Post by deadflowr on 2014-08-25
I meant for you to follow the guide in the code tag thread on how to use code tags, not to post in that thread.
I've moved that post over here.

Added: So I see you have a few files in home, some seem to be of a repeating nature.
I'm guessing you're trying to install this
[http://fenouille84.deviantart.com/art/Conky-Geek-inside-198858366](http://fenouille84.deviantart.com/art/Conky-Geek-inside-198858366)

---

### Post by firas2 on 2014-08-25
sorry  Miss understood  sorry

---

### Post by deadflowr on 2014-08-25
> **firas2 said:**
> sorry  Miss understood  sorry

No, re-reading what I originally posted, my wording was bad.
I apologize for that.

---

### Post by firas2 on 2014-08-25
thanks  and i have good news  it is working now

just an other Question please 

if i decide to download any other new one  who also has conkrc1  or 2 or what ever     how would i deal with this please

---

### Post by deadflowr on 2014-08-25
I love looking at various conkyrc files, either from posts in these forums, or elsewhere on the web.
Most are simply named conkyrc, when I get it i either change the names, or I make a new folder for it.
I usually make a folder for the more nutty ones, like anything sector11 posts, like this one
[http://ubuntuforums.org/showthread.php?t=281865&page=2291&p=13101992#post13101992](http://ubuntuforums.org/showthread.php?t=281865&page=2291&p=13101992#post13101992)

You can launch them from anywhere, as long as you use the -c option, otherwise known as --config, which directs conky to look for a file outside the default paths. The default paths are first the .conkyrc file in home, then, if none are found there, the /etc/conky/conky.conf file.

And when using the -c option the name doesn't matter at all, you can rename it anything you want.
If that makes sense...

---

### Post by firas2 on 2014-08-25
thank u sir   for the help  and finnaly i got it running ;)

no I better do a fast backup   because as u see i am totally new with Ubuntu and linux    

many thanks  and will start reading the link u provided about the tags 

thank u

---

