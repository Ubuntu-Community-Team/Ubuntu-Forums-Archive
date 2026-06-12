---
title: "I want to install GnoCHM to view CHM file in Dapper Drake"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by mzar720 on 2006-10-15
Hi Guys...
i have a small problem with Ubuntu 6.06.1 LTS (Dapper Drake)
 that makes me hate myself ](*,)  cause i cant solve it, i want to view chm file in Ubuntu 6.06.1 LTS (Dapper Drake)
 and when i searched i found a lot of tutorials and topics which talk about what i need and how to install gnochm to view CHM files but most of this pages suposed that the reader have an active internet connection which i dont have cause i use dialup connecton ( i cant get it to work in Dapper Drake)

i downloaded this packages: 

chmlib-dev_0.33-4_i386.deb
python-pychm_0.8.2-1_i386.deb
gnochm_0.9.4-2ubuntu2_all.deb

i try to install it by order but and i got some error message in terminal and i got GnoCHM shortcut in Application Menu and when i try to lunch it nothing happen and if i right click any chm file and try to open it whith gnochm nothing happen too...
so plz i wish if u could hlep with clear guide and consider that i have no internet connection.

any help will be greatful..

---

### Post by bodhi.zazen on 2006-10-16
```
sudo aptitude install xchm
```

---

### Post by Jucato on 2006-10-16
or use Synaptic, look for gnochm (or xchm) and install it from there. It makes life a lot easier.

---

### Post by mzar720 on 2006-10-16
> **bodhi.zazen said:**
> ```
sudo aptitude install xchm
```

@bodhi.zazen
i try this command and i cant get it to install cause xchm is not included in Ubuntu 

6.06. and this what i get in terminal after type this command:
```
mahmoud@Ubuntu:~$ sudo aptitude install xchm

Password:

Reading package lists... Done
Building dependency tree... Done
Initializing package 

states... Done
Building tag database... Done
Couldn't find any package whose name 

or description matched "xchm"
No packages will be installed, upgraded, or 

removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not 

upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
mahmoud@Ubuntu:~$


 
```

---

### Post by mzar720 on 2006-10-16
> **Jucato said:**
> or use Synaptic, look for gnochm (or xchm) and install it from there. It makes life a lot easier.

@Jucato
i try and i dont found it in Synaptic (both gnochm or xchm)

Please guys i want to install GnoCHM not Xchm and i dont have an active internet connection

thanks for ur help

---

### Post by po0f on 2006-10-16
mzar720,

Have you tried double-clicking the *.debs?

---

### Post by mzar720 on 2006-10-16
> **po0f said:**
> mzar720,

Have you tried double-clicking the *.debs?
i did but i get error message and cant install it by double clicking so i try the classic way to install deb packages.

---

### Post by bodhi.zazen on 2006-10-16
> **mzar720 said:**
> @Jucato
i try and i dont found it in Synaptic (both gnochm or xchm)

Please guys i want to install GnoCHM not Xchm and i dont have an active internet connection

thanks for ur help

The last time I tried I could not install GnoCHM. I do not recall why, it was a few months age....

At any rate here is a link to [Gnochm](http://packages.ubuntu.com/dapper/gnome/gnochm)
You will need to download all those .deb files and dependencies....


xchm works well and is what I am using because I could not install Gnochm.

Here is the link to 

[xchm](http://packages.ubuntu.com/dapper/x11/xchm)

[how to install xchm](http://ubuntuguide.org/wiki/Dapper#How_to_install_Compiled_HTML_Help_.28CHM.29_Viewer_.28xCHM.29)

This how to uses apt-get so you will need internet access and to enable some repositories. The above link shows how that is done.

Otherwise, as with gnochm, you will need to download and install all the .deb files and dependencies from the first xchm link.

8-)

---

### Post by PriceChild on 2006-10-16
If you have isntalled the program, but it won't open, it might be nice for you to paste us the error message returned when you open it in terminal.

---

### Post by bodhi.zazen on 2006-10-16
LOL :lol: Try this:[ Howto: GnoCHM](http://ubuntuforums.org/showthread.php?t=81510)

---

### Post by mzar720 on 2006-10-16
> **bodhi.zazen said:**
> The last time I tried I could not install GnoCHM. I do not recall why, it was a few months age....

At any rate here is a link to [Gnochm](http://packages.ubuntu.com/dapper/gnome/gnochm)
You will need to download all those .deb files and dependencies....


xchm works well and is what I am using because I could not install Gnochm.

Here is the link to 

[xchm](http://packages.ubuntu.com/dapper/x11/xchm)

[how to install xchm](http://ubuntuguide.org/wiki/Dapper#How_to_install_Compiled_HTML_Help_.28CHM.29_Viewer_.28xCHM.29)

This how to uses apt-get so you will need internet access and to enable some repositories. The above link shows how that is done.

Otherwise, as with gnochm, you will need to download and install all the .deb files and dependencies from the first xchm link.

8-)

thanks bodhi.zazen for ur helpful replay i downloaded Gnochm and all dependencies from the link u add and i finally install gnochm and i capture this pic for gnochm 

[[IMG]http://img473.imageshack.us/img473/1691/chmviewerubuntuhackskj6.th.png[/IMG]](http://img473.imageshack.us/my.php?image=chmviewerubuntuhackskj6.png)

---

### Post by mzar720 on 2006-10-16
> **PriceChild said:**
> If you have isntalled the program, but it won't open, it might be nice for you to paste us the error message returned when you open it in terminal.

@ PriceChild
i think now i have no problem with installing gnpchm but can You tell me Please how can i lunch applications from terminal...

---

### Post by mzar720 on 2006-10-16
> **bodhi.zazen said:**
> LOL :lol: Try this:[ Howto: GnoCHM](http://ubuntuforums.org/showthread.php?t=81510)

thanks bodhi.zazen it is a very helpful guide that help me a lot before i post this thread.

thanks again for everyone hear....

---

### Post by bodhi.zazen on 2006-10-16
> **mzar720 said:**
> thanks bodhi.zazen for ur helpful replay i downloaded Gnochm and all dependencies from the link u add and i finally install gnochm and i capture this pic for gnochm 

[[IMG]http://img473.imageshack.us/img473/1691/chmviewerubuntuhackskj6.th.png[/IMG]](http://img473.imageshack.us/my.php?image=chmviewerubuntuhackskj6.png)

Thanks a lot mzar720 #-o
[indent][indent].... Now I'll have to install gnochm myself !! :p[/indent][/indent]

congratulations !! =D>

---

### Post by mzar720 on 2006-10-16
> **bodhi.zazen said:**
> Thanks a lot mzar720 #-o
[indent][indent].... Now I'll have to install gnochm myself !! :p[/indent][/indent]

congratulations !! =D>

you are welcome and thanks :)  again for your help and i wish u a good luck with GnoCHM ](*,)

---

