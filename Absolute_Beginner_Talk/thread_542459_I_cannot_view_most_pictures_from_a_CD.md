---
title: "I cannot view most pictures from a CD"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-09-04
I have a CD full of pictures. The icons of most pictures have padlocks on them (see snapshot). On windows, I can view the pictures, but whenever I open them (the ones with padlocks on the icons) on Gwenview, no picture do come out. Also, I have noticed that those with padlocks have no metainfo.

See the screenshots to see the padlocks I am referring to.

---

### Post by deadgobby on 2007-09-04
I do not see a attachment of your screen shot, yet I know what you may be talking about. If there is a lock icon on the CD. The author may have use a windows machine or so on. You can move the pic to the desktop. Then go into the terminal and change the owner ship to you. So from the terminal 
cd Desktop
ls ( that is to list all what is on your desktop)
sudo chown yourusername file name

so example

sudo chown meuser beach.jpeg

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_ownership](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_ownership)

---

### Post by wersdaluv on 2007-09-04
The problem is that I cannot even copy the images with locks in their icons. When I copied a locked picture to my desktop, the attached error message came out.

---

