---
title: "[SOLVED] Xubuntu powerpc desktop icons disappear"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by Leslie Viljoen on 2008-11-14
Hi people

If your desktop icons disappear frequently and you have to go into settings and click on "allow xfce to manage my desktop" to get them back, you probably have the famous segmentation fault problem discussed here:
[http://ubuntuforums.org/showthread.php?t=977120](http://ubuntuforums.org/showthread.php?t=977120)

I have uploaded fixed packages here:

[http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335ca14ae01059dac3289](http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335ca14ae01059dac3289)

1. Download them to a new folder
2. In a terminal, do 'sudo dpkg -i *deb' in the new folder

If you get a complaint about dependencies: 
1. sudo apt-get -f install
2. sudo dpkg -i *deb


- Les

---

