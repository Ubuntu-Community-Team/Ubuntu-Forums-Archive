---
title: "How to consolidate several thousand files from several hundred folders"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-05-13
Ok, so here's my issue. I had a hard drive that was corrupted, and I am now using PhotoRec to recover all of the images, HTML files, and text files from the drive. PhotoRec is putting the files into several hundred folders titled /home/brendon/recup_dir.*/ with the star being a number. What I would like to do is consolidate all of these files into one folder from these several hundred folders, and from there most likely split the files again based on filetype, so that I can dig through them and delete what I don't need. If there is a way to consolidate this all into one step (such as a script that would combine all of the steps) it would be great, but I don't expect anyone to invest the massive amount of required time for me. Any help would be greatly appreciated!!!

---

### Post by Kal9001 on 2007-05-13
A script i think will very easily do all that for you. unfortunatly Ive had to experiance writing scripts....so have a look at:

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

and see if you cant bodge one of there example scripts or if you pick up up quick enough then write your own :)

---

### Post by brennydoogles on 2007-05-13
> **Kal9001 said:**
> A script i think will very easily do all that for you. unfortunatly Ive had to experiance writing scripts....so have a look at:

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

and see if you cant bodge one of there example scripts or if you pick up up quick enough then write your own :)

Unfortunately I think this is beyond my grasp, but if anyone who is experienced and bored wants to help you are more than welcome!!

---

### Post by Bachstelze on 2007-05-13
No need for even a bash script here :

```

cd
mkdir recupFiles
mv recup_dir.*/* recupFiles
```

Then all the files that were in the recup_dir* folders will be moved in the recupFiles folder. Then if you want to split them based on filetype, you can do for example :

```

mkdir images
mv recupFiles/*.jpg images
mkdir music
mv recupFiles/*.ogg music

```

and so on...

---

### Post by Nekiruhs on 2007-05-13
Or.. as this hasnt been suggested yet 
```
tar -cvzf /home/brendan/recup_dir.* RecoverdFiles.tar.gz
```
Should give you a compressed archive of pics, could save alot of space. (Someone please correct me, as I am typing this from my windows half and cant read 'man tar')

---

### Post by Bachstelze on 2007-05-13
Your syntax is wrong, the archive name goes first, before the files to compress. And anyway, this would not solve the problem as the files still would be split in different folders.

---

### Post by Nekiruhs on 2007-05-13
Thanks, I couldn't remeber which came first.

---

### Post by brennydoogles on 2007-05-14
> **HymnToLife said:**
> No need for even a bash script here :

```

cd
mkdir recupFiles
mv recup_dir.*/* recupFiles
```

Then all the files that were in the recup_dir* folders will be moved in the recupFiles folder. Then if you w.ant to split them based on filetype, you can do for example :

```

mkdir images
mv recupFiles/*.jpg images
mkdir music
mv recupFiles/*.ogg music

```

and so on...


Hymntolife, it seems that you have always been and will always be my hero  =D> . I may take all of these steps and write them into a script so that I can better learn scripting, but thanks so much for your help!!

---

### Post by brennydoogles on 2007-05-14
> **HymnToLife said:**
> No need for even a bash script here :

```

cd
mkdir recupFiles
mv recup_dir.*/* recupFiles
```

Then all the files that were in the recup_dir* folders will be moved in the recupFiles folder. Then if you want to split them based on filetype, you can do for example :

```

mkdir images
mv recupFiles/*.jpg images
mkdir music
mv recupFiles/*.ogg music

```

and so on...

ok, so we hit an issue... too many files 
```
brendon@desktop:~$ mkdir winsaves
brendon@desktop:~$ mv -v recup_dir.*/* winsaves/
bash: /bin/mv: Argument list too long

```

I know there is a way to create a list of files and feed them one by one into the mv command... how would I do that?? There are 139 folders with ~500 files in each. Any help would be greatly appreciated!!

---

### Post by brennydoogles on 2007-05-14
ok, so in an IM chat Hymntolife was able to help me out.by typing
```
for i in recup_dir.*/*; do mv -v $i /home/brendon/winsaves/; done
```

and that allowed me to move the almost 40,000 recovered files from almost 150 folders into one. From there I will be able to do

```
for i in winsaves/*.jpg; do mv -v $i /home/brendon/winsaves/jpg/; done
```
in order to organize the files by filetype. Thanks Hymntolife!!

---

