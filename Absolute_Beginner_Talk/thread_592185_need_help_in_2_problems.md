---
title: "need help in 2 problems"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Bluduntu on 2007-10-26
Hi,i hope this is right thread to post this,i dont know how much noob i am,but i have a problem,i know its discussed,but still maybe anybody can make me more clear how to do this.
ok so, problem:
i try to make own ubuntu 7.10 based distro with recunstructor,but i cant figure out,how make usplash screen,i add here files what i want to use.
[http://www.speedyshare.com/338201338.html]("http://www.speedyshare.com/338201338.html")
i opened terminal in reconstructor and added these usplash files in reconstructor root,but what commands i must use to make uspalsh.so files? Can anybody please explain it,i readed many how- tos,but still dont understand how to make these .so files.
And second problem,maybe its not right place to ask it,but i hope its ok.
How  can i remove from top panel evolution and help icons? and add other icons there?
i mean,when i boot live cd,then there is no evolution and help icon anymore,can this be done?
thank you very much

---

### Post by meborc on 2007-10-26
have you checked out this [http://uck.sourceforge.net/](http://uck.sourceforge.net/) and this [https://wiki.ubuntu.com/LiveCDCreator](https://wiki.ubuntu.com/LiveCDCreator)

not sure, as i never tried to do this miself, but ubuntu wiki has a lot of reasources... and i have heard it been done before :D:D:D good luck

---

### Post by Bluduntu on 2007-10-26
> **meborc said:**
> have you checked out this [http://uck.sourceforge.net/](http://uck.sourceforge.net/) and this [https://wiki.ubuntu.com/LiveCDCreator](https://wiki.ubuntu.com/LiveCDCreator)

not sure, as i never tried to do this miself, but ubuntu wiki has a lot of reasources... and i have heard it been done before :D:D:D good luck
this is not what i asked,but its very useful,i didnt now about Ubuntu Customization Kit,it seems to be better then reconstructor.
Big thanks to you,anyway,still waiting answer about usplash building
tnx

---

### Post by qamelian on 2007-10-26
Here is a link to the Ubuntu wiki page explaining how to create or customize usplash.
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by Bluduntu on 2007-10-26
> **qamelian said:**
> Here is a link to the Ubuntu wiki page explaining how to create or customize usplash.
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Hi tnx,but i know already this howto,my point is,i didnt understand it,can you explain it
example these commands:
cp yourimage.png usplash-artwork.png
pngtobogl usplash-artwork.png > usplash-artwork.c
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o yourimage-splash.so

i have in my usplash folder following files bleu_800_600.png,bleu_1024_576_cropped.png,
bleu_1024_768.png,bleu rayo.png,orange_1024_576.png,bleu-theme.c,helvB10.bdf,Makefile,
throbber_back.png,throbber_fore.png,
i added these files in first post also

question is,how can i make usplash from these files,do i must write in terminal 

cp  bleu_800_600.png bleu_1024_576_cropped.png 
bleu_1024_768.png bleu rayo.png orange_1024_576.png bleu-theme.c 
throbber_back.png,throbber_fore.png,
pngtobogl bleu_800_600.png bleu_1024_576_cropped.png 
bleu_1024_768.png bleu rayo.png orange_1024_576.png bleu-theme.c > usplash-artwork.c
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o yourimage-splash.so

or how? and will this guide work in latest ubuntu release?

big tnx

---

### Post by qamelian on 2007-10-26
That's right. You need to enter those commands in a terminal. Unless something has changed dramatically, those instructions should still be valid.

---

### Post by Bluduntu on 2007-10-26
> **qamelian said:**
> That's right. You need to enter those commands in a terminal. Unless something has changed dramatically, those instructions should still be valid.
ok i try it,just one more question,to i must add make file too there?
cp bleu_800_600.png bleu_1024_576_cropped.png
bleu_1024_768.png bleu rayo.png orange_1024_576.png bleu-theme.c
throbber_back.png,throbber_fore.png,
pngtobogl bleu_800_600.png bleu_1024_576_cropped.png
bleu_1024_768.png bleu rayo.png orange_1024_576.png bleu-theme.c [COLOR="Red"]make[/COLOR] > usplash-artwork.c
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o yourimage-splash.so


and can anybody please answer my second question
How can i remove from top panel evolution and help icons? and add other icons there?
i mean,when i boot live cd,then there is no evolution and help icon anymore,can this be done?
big tnx again

---

### Post by Bluduntu on 2007-11-11
still in trouble with usplash,please somebody help!
i added image there,can somebody please tell me how to make usplash from these files,what commands i must use,because i get black screen all the time,i think i did something wrong?
[http://imgbolt.com/public/pview/41438/Screenshot.png]("http://imgbolt.com/public/pview/41438/Screenshot.png")
i just cant figure it  out:(

---

