---
title: "Im loving it !! just need to change keyboard and PDA"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-07-30
Hi all 

Oka nearly 2 weeks using Xubuntu, really nice working VERY well. Fast stable, makes this old machine look positively modern

I have a few things to Iron out, to make it perfect I ll list them here then work through them one by one.

   a,  PDA How do you connect a PDA to  Xubunto ( I have installed multi synch, but it wants a user id no  whats that , where is that on a pda , ,,clie nx60 palm 5 .  I think thats all thats needed.

   B  Swapping  keyboards I want to swap the keyboard to Japanese , I have a japanese computer so the @ is in the wrong place.  I key board code jap106 ??   On the windows I use alt shift and the ime changes , now I have installed the language pack and if I restart the session and change llanguages it work fantastically everythings in Japanese , 

  c  Would like to use autocad with wine  but thats not important right now as I will do that when I up grade the main machine ...to ubuntu of course !!!!

Finally a big thanks , I really like the way Ican have all my info at the top ofthe screen leaving the viewing area quite large, in a panal on the top screen it tells me how the cpu is going , memory , what programs are minimized , and there is a mail I havent checked ! great.

Kind regards 
Stephen

---

### Post by Paerez on 2006-07-30
I know how to do a:
use JPilot. It's the best.

---

### Post by basilwatson on 2006-07-31
using Jpilot but nothing is synching , How do a PDA and computer I dentify themselves , User name , But what is this Id number ??

There is a number on the hotsynch page of the clie, but it says computer no , its the only one I can find 

I used that, but it still didnt synch 

is ther something I am missing ?

Stephen

---

### Post by adamkane on 2006-07-31
Keyboard:
[http://www.ubuntuforums.org/showthread.php?t=102760](http://www.ubuntuforums.org/showthread.php?t=102760)
[http://www.ubuntuforums.org/showthread.php?t=102778](http://www.ubuntuforums.org/showthread.php?t=102778)
[http://www.ubuntuforums.org/showthread.php?t=129860](http://www.ubuntuforums.org/showthread.php?t=129860)

---

### Post by basilwatson on 2006-07-31
Yes I looked for something like that and I am using Xubuntu which doesnt have what those links said to follow 

System / preferences/ keyboard .. or what ever it was 

 The only thing I could see was #sudo x-system xorg  ( Ive written it down somewhere !

But that asks for a keyboar lay out but I dont know what to type 

Jap106 ? I have a Japanese computer 

 So I still havent managed to swap keyboards.. 

Sorry its back to the drawing board 

Stephen

---

### Post by Paerez on 2006-07-31
The ID number is stored on the palm and you shouldn't have to set it, it will be set on a sync. With jpilot, you have to set the path to the device the palm was connected to. So plug in the palm and type:
```
dmesg | tail
```
and you will the the palm get connected to 2 devices:
ttyUSBn and ttyUSB(n+1)
for example: ttyUSB0 and ttyUSB1. Take the greater one, and put it in for the device in jpilot (/dev/ttyUSB1). You have to check every time you plug in, or make a udev rule for palm pilots.

---

### Post by encho on 2006-07-31
Those links are for gnome, I think we are talking about xfce here. For changing keyboard settings in xubuntu, use keyboard switcher applet. If ur using latest beta (from edgy repositories), keyboard layouts are broken at the moment.

check
[http://www.ubuntuforums.org/showthread.php?t=82213&highlight=arabic+xfce](http://www.ubuntuforums.org/showthread.php?t=82213&highlight=arabic+xfce)
for additional layouts.

---

### Post by basilwatson on 2006-08-01
Hi folks 
Well it sort of changes languages, I cut and pasted the command line as per arabic and changed the ar to jp, and the little flag up on the tool bar is Japanese 

As of yet. I cant find the key combination to swap between languages shift shift ctrl,space etc, I can swap if I click on the icon and go properties ( there are 2 in the text dialogue box jp and jp one is english the other is Japanese ) 

Sooo Nearly there ! 

Any ideas 

Stephen
Sorry wrong forum , Ill repost in beginners Sorry

---

### Post by basilwatson on 2006-08-01
Hi folks 
Well it sort of changes languages, I cut and pasted the command line as per arabic and changed the ar to jp, and the little flag up on the tool bar is Japanese 

As of yet. I cant find the key combination to swap between languages shift shift ctrl,space etc, I can swap if I click on the icon and go properties ( there are 2 in the text dialogue box jp and jp one is english the other is Japanese ) 

Sooo Nearly there ! 

Any ideas 

Stephen

---

### Post by encho on 2006-08-04
Check the end of the post ^

I think someone was asking about ctrl-shift combination.

---

