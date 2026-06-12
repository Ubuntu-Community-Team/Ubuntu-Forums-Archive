---
title: "HOW TO install anything in ubuntu 7.10"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by kratosal on 2008-03-16
i mean i just can't install anything........  on  ubuntu  or  any  othe  linux  distro.....  i  got  acd  from  an  it  mag.......  which  had  softwares  for  windows  and  linux  both  but  in  synapmatic  package manager when i tried  to  add  third  party software and  add  a  cd- rom,  it  was  unable  to  retrive  it  giving error  msg......... it  happened  to  every  disc...............  please  hel  me,    guide me by  teaching  me  to  install  codecs  to  listen  mp3 on  my  system,  i  am  confused  with  vlc as i the  site so many  things  are  given  to  download......

also  when  you  install  something  on linux,  by default  where  the  software  resides.........   and   how  could  i  install  softwares  which  resideon  my desk top and  not  on  cd=rom  with  tar.gz  format  and  others  like  that.........


i don't have any internet connection

---

### Post by Locutus_of_Borg on 2008-03-16
assuming you have an internet connection, open a terminal ad type "sudo apt-get install <name of package"

i.e. to install zsnes enter ```
sudo apt-get install zsnes
```

they are often downloaded to /usr/bin it seems, but i imagine its different depending on the application


alternatively you can download packages through a web browser and install them with ```
dpkg -i <package name>
```
if you are downloading archives (.tar.gz etc) extract the archive depending on its type, enter the directory containing the source, and in a terminal enter "./configure" then "make" and finally "sudo make install"

if you have all dependencies met, this will compile and install the program

---

### Post by adi_das on 2008-03-16
This will help u.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by mikewhatever on 2008-03-16
Here you go:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

### Post by bumanie on 2008-03-16
Along with the above, it is alos important to enable the softwre repositories. System --> Administration --> Software Sources. Ensur the first 4 boxes are ticked and then check third party tab and tick anything that may be there. Also it is a good idea to update your apt/sources.list
Follow this guide [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

