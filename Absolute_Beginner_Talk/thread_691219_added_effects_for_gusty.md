---
title: "added effects for gusty"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by boboyo on 2008-02-08
a long time ago, i wanted 3d windows and a guy gave me this site
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)
now, id like to have atlantis and snow and alot of things like that
on the site, theres the place where to download it but it doesnt say how to compile it
it says it only for 3d windows and freewins
can someone tell me how to install them?

---

### Post by ashmew2 on 2008-02-10
Well I think that you have to first extract all of the archives (the tarballs in .tar format) to the /compiz/ directory , as the site says).
Just use this command : (You can copy paste all of these at once into the terminal , no need of executing it line by line)
```


  tar -xf '/tmp/3d.tar.gz' -C ~/compiz/     
  tar -xf '/tmp/atlantis2.tar.gz' -C ~/compiz/      
  tar -xf '/tmp/snow.tar.gz' -C ~/compiz/                       
  tar -xf '/tmp/stars.tar.gz' -C ~/compiz/                         
  tar -xf '/tmp/atlantis.tar.gz' -C ~/compiz/                          
  tar -xf '/tmp/screensaver.tar.gz' -C ~/compiz/                         
  tar -xf '/tmp/anaglyph.tar.gz' -C ~/compiz/                          
  tar -xf '/tmp/wallpaper.tar.gz' -C ~/compiz/                         
  tar -xf '/tmp/tile.tar.gz' -C ~/compiz/                          
  tar -xf '/tmp/freewins.tar.gz' -C ~/compiz/                          
  tar -xf '/tmp/fireflies.tar.gz' -C ~/compiz/                          
  tar -xf '/tmp/photowheel-0.6.tar.gz' -C ~/compiz/                        
  tar -xf '/tmp/snowglobe.tar.gz' -C ~/compiz/   
```                      
         


After that : (In the terminal) : 
```

cd ~/compiz/
cd 3d
make
make install
cd ..
cd <put name of the next directory here>
make
make install
cd ..
```

and so on. Do this for all directories.

I think thats all there's to it.


Btw , I am also downloading the files (thanks for the link) and Ill get back to you if I encounter any errors. Although I'd love to hear from you again :P

---

### Post by ashmew2 on 2008-02-10
OK Tested it as well. Works Flawlessly. Needs a good graphics card though for all the uber cool effects.

---

### Post by boboyo on 2008-02-10
cd ~/compiz/
cd 3d
make
make install
cd ..
cd <put name of the next directory here>
make
make install
cd ..

and so on. Do this for all directories.

I think thats all there's to it.



ashmew, what did u mean by cd ..?

---

### Post by ashmew2 on 2008-02-12
cd means change directory...
I give you these commands to be run in the terminal..
wait ill put the proper tags,

When you do cd ~/name of directory/ 
It takes you into that directory.. and when you do 

cd ..

it takes you one directory back.

---

