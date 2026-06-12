---
title: "unzipping a file ?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by keith whitehouse on 2006-05-20
Hi there,
this is my first post, and like everyone else here I am new to Linux. I have managed to get one of my Windows programs (Superbase) running under wine, but I am stuck on the simple thing of running a batch file, as I have found that my old dos .bat files do not function.
I have a file on my desktop named new_burr.zip and it contains anything from 10 to 100 seperate files. I wish to unarchive them and put them into
/keith/.wine/drive_c/program files/racing and name the file C1 (no extension). Any help would be appreciated

best regards  Keith

---

### Post by Googler on 2006-05-20
i think the easiest way is to right click on the file and choose extract

---

### Post by mostwanted on 2006-05-20
[http://monkeyblog.org/ubuntu/videos/Extract_here.gif](http://monkeyblog.org/ubuntu/videos/Extract_here.gif)

---

### Post by glotz on 2006-05-20
That's a spanking nice gif, did you make it yourself? How?

---

### Post by mostwanted on 2006-05-20
Used Byzanz. It's really nice - GIF is good format because it's supported in most browsers (IE does have show artifacts sadly) and the software patent will expire next year making it good in the eyes of RMS as well :p

---

### Post by keith whitehouse on 2006-05-20
Hi there,
right clicking the new_burr.zip icon and unarchiving here only gives me a new icon with the 100 files all still as individual files. I need to unzip the files (all 100of them) and make one big file containing all of the files and named C1.

best regards keith

---

### Post by glotz on 2006-05-20
Thanks mostwanted, I'll be fooling around with it soon! I do some IT support and that looks like a great tool!

---

### Post by kaamos on 2006-05-20
This sucks as I have absolutely no experience with bash scripts, but you should be able to get the general idea
```

mkdir temp
cp burr.zip temp/
cd temp
unzip burr.zip
rm burr.zip
for f in *.zip;
     do mkdir temp2;     
     mv f temp2/;
     cd temp2/;
     unzip f;
     rm f;
     cat * >> /keith/.wine/drive_c/program files/racing/C2
     cd ..;
     rm -rf temp2/;
done;
cd ..
rm -rf temp

```

---

### Post by keith whitehouse on 2006-05-20
thanks kaamos,

I will have a good look at your post and try to understand it, and then I will give it a try.

many thanks keith

---

### Post by keith whitehouse on 2006-05-21
Hi Kaamos,

many thanks for the advice. I tried it and it did not work very well so I made a few changes to it and it now looks like

cd /home/keith/Desktop
mkdir temp
cp NEW_BURR.ZIP temp/
cd temp
unzip NEW_BURR.ZIP
rm NEW_BURR.ZIP
for f in *.ZIP;
     do mkdir temp2;     
     mv f temp2/;
     cd temp2/;
     unzip f;
     rm f;
     cat * >> /keith/.wine/drive_c/Program Files/Racing/C1
     cd ..;
     rm -rf temp2/;
done;
cd ..
rm -rf temp

in "terminal" it gives the following

keith@ubuntu:~$ cd /home/keith/Desktop
keith@ubuntu:~/Desktop$ mkdir temp
keith@ubuntu:~/Desktop$ cp NEW_BURR.ZIP temp/
keith@ubuntu:~/Desktop$ cd temp
keith@ubuntu:~/Desktop/temp$ unzip NEW_BURR.ZIP
Archive:  NEW_BURR.ZIP
  inflating: BAN_20_1.GLD
  inflating: BAN_20_2.GLD
  inflating: BAN_20_3.GLD
  inflating: BAN_20_4.GLD
  inflating: BAN_20_5.GLD
  inflating: BAN_20_6.GLD
  inflating: BAN_20_7.GLD
  inflating: NBU_20_1.GLD
  inflating: NBU_20_2.GLD
  inflating: NBU_20_3.GLD
  inflating: NBU_20_4.GLD
  inflating: NBU_20_5.GLD
  inflating: NBU_20_6.GLD
  inflating: NBU_20_7.GLD
  inflating: NBU_20_8.GLD
  inflating: NTT_20_1.GLD
  inflating: UTT_20_4.GLD
  inflating: UTT_20_5.GLD
  inflating: UTT_20_6.GLD
  inflating: WOR_20_1.GLD
  inflating: WOR_20_2.GLD
  inflating: WOR_20_3.GLD
  inflating: WOR_20_4.GLD
  inflating: WOR_20_5.GLD
  inflating: WOR_20_6.GLD
  inflating: PUN_20_1.GLD
  inflating: PUN_20_2.GLD
  inflating: PUN_20_3.GLD
  inflating: PUN_20_4.GLD
  inflating: PUN_20_5.GLD
  inflating: PUN_20_6.GLD
  inflating: PUN_20_7.GLD
  inflating: RIP_21_3.GLD
  inflating: RIP_21_4.GLD
  inflating: RIP_21_5.GLD
  inflating: RIP_21_6.GLD
  inflating: RIP_21_7.GLD
  inflating: NAV_21_1.GLD
  inflating: NAV_21_2.GLD
  inflating: NAV_21_3.GLD
  inflating: NAV_21_4.GLD
  inflating: NAV_21_5.GLD
  inflating: NAV_21_6.GLD
  inflating: NAV_21_7.GLD
  inflating: GOW_21_1.GLD
  inflating: GOW_21_2.GLD
  inflating: GOW_21_3.GLD
  inflating: GOW_21_4.GLD
  inflating: GOW_21_5.GLD
  inflating: GOW_21_6.GLD
  inflating: GOW_21_7.GLD
  inflating: FKN_21_1.GLD
  inflating: FKN_21_2.GLD
  inflating: FKN_21_3.GLD
  inflating: FKN_21_4.GLD
  inflating: FKN_21_5.GLD
  inflating: FKN_21_6.GLD
  inflating: FKN_21_7.GLD
  inflating: MAR_21_1.GLD
  inflating: MAR_21_2.GLD
  inflating: MAR_21_3.GLD
  inflating: MAR_21_4.GLD
  inflating: MAR_21_5.GLD
  inflating: MAR_21_6.GLD
  inflating: MAR_21_7.GLD
  inflating: RIP_21_1.GLD
  inflating: RIP_21_2.GLD
  inflating: NTT_20_2.GLD
  inflating: NTT_20_3.GLD
  inflating: NTT_20_4.GLD
  inflating: NTT_20_5.GLD
  inflating: NTT_20_6.GLD
  inflating: NTT_20_7.GLD
  inflating: THR_20_1.GLD
  inflating: THR_20_2.GLD
  inflating: THR_20_3.GLD
  inflating: THR_20_4.GLD
  inflating: THR_20_5.GLD
  inflating: THR_20_6.GLD
  inflating: THR_20_7.GLD
  inflating: UTT_20_1.GLD
  inflating: UTT_20_2.GLD
  inflating: UTT_20_3.GLD
keith@ubuntu:~/Desktop/temp$ rm NEW_BURR.ZIP
keith@ubuntu:~/Desktop/temp$ for f in *.ZIP;
>      do mkdir temp2;
>      mv f temp2/;
>      cd temp2/;
>      unzip f;
>      rm f;
>      cat * >> /keith/.wine/drive_c/Program Files/Racing/C1
>      cd ..;
>      rm -rf temp2/;
> done;
mv: cannot stat `f': No such file or directory
unzip:  cannot find or open f, f.zip or f.ZIP.
rm: cannot remove `f': No such file or directory
bash: /keith/.wine/drive_c/Program: No such file or directory
keith@ubuntu:~/Desktop/temp$ cd ..
keith@ubuntu:~/Desktop$ rm -rf temp

looks to be nearly there but I do not understand what the line 

keith@ubuntu:~/Desktop/temp$ for f in *.ZIP; is and what happens after that.

my apologies for being such a slow learner

best regards keith

---

