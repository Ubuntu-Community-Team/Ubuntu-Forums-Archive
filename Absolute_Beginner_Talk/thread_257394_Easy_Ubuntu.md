---
title: "Easy Ubuntu"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-14
I have found Easy Ubuntu impossible and really would like to use it is there anyone out there who could help me

Thanks

Tobster

AKA Toby

---

### Post by Drakkor on 2006-09-14
At what point exactly are you having problems ?

---

### Post by Tobster on 2006-09-14
all of it!  Is does seem to do what is on the Easy Ubuntu Web site

---

### Post by Iowan on 2006-09-14
Not that you can't find help here, but there's a sub-forum just for Easy Ubuntu [here.]("http://www.ubuntuforums.org/forumdisplay.php?f=86")

---

### Post by Tobster on 2006-09-14
toby@toby-desktop:~$ [http://tinyurl.com/gwrdf](http://tinyurl.com/gwrdf)
bash: [http://tinyurl.com/gwrdf:](http://tinyurl.com/gwrdf:) No such file or directory
toby@toby-desktop:~$

---

### Post by Drakkor on 2006-09-14
I have found that the ```
sudo python easyubuntu.in
``` doesn't work because I don't have that file in the easyubuntu folder but ```
sudo python easyubuntu.py
``` works ! 
:p

---

### Post by RobsterUK on 2006-09-14
> **Tobster said:**
> toby@toby-desktop:~$ [http://tinyurl.com/gwrdf](http://tinyurl.com/gwrdf)
bash: [http://tinyurl.com/gwrdf:](http://tinyurl.com/gwrdf:) No such file or directory
toby@toby-desktop:~$

You seem to be trying install the package version of EasyUbuntu. You can just navigate to it in your browser and select open with package manager

---

### Post by Tobster on 2006-09-14
Thanks I got the files now but how do i install them? :)

---

### Post by Drakkor on 2006-09-14
Try this:
```
wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz
tar -zxf easyubuntu-3.023.tar.gz
cd easyubuntu
sudo python easyubuntu.in


```

Like I said before sudo python easyubuntu.in is not found but sudo python easyubuntu.py works fine !

---

### Post by Drakkor on 2006-09-14
You should be able to just double click the .deb file to install, but I think you have to run easy ubuntu from the termial.

---

### Post by Tobster on 2006-09-14
file:///home/toby/Desktop/Screenshot.png

---

### Post by Tobster on 2006-09-14
sudo python easyubuntu.py -does not work because it ask for a password but will not let you type it in:-\"

---

### Post by Tobster on 2006-09-14
It should be called impossible Ubuntu :)

But i do like Ubuntu - apart from this

---

### Post by haxer on 2006-09-14
:S what hmm... the password should not be seen just type in the password and it will still looks like this Password: then enter it then press enter!!

---

### Post by Tobster on 2006-09-14
the screen shot is were im at. Thanks for your help have 2 Easy Ubuntu files. What next?

---

### Post by haxer on 2006-09-14
Go to terminal copy this text right click copy then right click inside terminal window and select paste... 

wget[http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
tar -zxf easyubuntu-3.023.tar.gz
cd easyubuntu
sudo python easyubuntu.in


Then it will ask you for ur password then you type it in then press enter and the password wont be seen like this ********** or anything at all you just type it in the root password then press enter once again you will not see that you type in your password!!

---

### Post by Drakkor on 2006-09-14
```
cd easyubuntu
sudo python easyubuntu.in

```
**OR If can't find**
```
cd easyubuntu
sudo python easyubuntu.py

```

---

### Post by haxer on 2006-09-14
ok try his answer and remember you wont see when you type in password!!

---

### Post by Drakkor on 2006-09-14
Yeah,that throws a lot of people,lol :p

---

### Post by Drakkor on 2006-09-14
Like this:

---

### Post by Tobster on 2006-09-14
toby@toby-desktop:~$ wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
--21:47:51--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
           => `easyubuntu-3.023.tar.gz.1'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92,653 (90K) [application/x-tar]

100%[====================================>] 92,653       485.47K/s

21:47:52 (483.76 KB/s) - `easyubuntu-3.023.tar.gz.1' saved [92653/92653]

toby@toby-desktop:~$ tar -zxf easyubuntu-3.023.tar.gz
toby@toby-desktop:~$ cd easyubuntu
toby@toby-desktop:~/easyubuntu$ sudo python easyubuntu.in
Password:


That what I get now but it will not let you type a password

---

### Post by RobsterUK on 2006-09-14
> **Tobster said:**
> That what I get now but it will not let you type a password

As mentioned before, it will not show anything when you type the password, you just have to have faith that its taking in what you type and press enter.

Apart from that the rest of what you posted looks good....nearly there :)

---

### Post by haxer on 2006-09-14
Nice and calm now alex :P hehe.. as i said you will only see this 

Password:[here you type your password then enter not shown but it will be their any way!!]

---

### Post by Tobster on 2006-09-14
toby@toby-desktop:~$ wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
--21:47:51--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
           => `easyubuntu-3.023.tar.gz.1'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92,653 (90K) [application/x-tar]

100%[====================================>] 92,653       485.47K/s

21:47:52 (483.76 KB/s) - `easyubuntu-3.023.tar.gz.1' saved [92653/92653]

toby@toby-desktop:~$ tar -zxf easyubuntu-3.023.tar.gz
toby@toby-desktop:~$ cd easyubuntu
toby@toby-desktop:~/easyubuntu$ sudo python easyubuntu.in
Password:

What is the password?

---

### Post by haxer on 2006-09-14
And dont forget to press ENTER the biggest buttom on the keybord often :) :-\"

---

### Post by haxer on 2006-09-14
your root password !! the password you typed in when you installed it!!

---

### Post by Drakkor on 2006-09-14
"Swordfish"

---

### Post by haxer on 2006-09-14
If you dont know what it is try this [http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)

---

### Post by Drakkor on 2006-09-14
Your same login password

---

### Post by RobsterUK on 2006-09-14
> **Tobster said:**
> What is the password?
Your user password, that you use to login when you boot up the computer.

---

### Post by haxer on 2006-09-14
Dont be meen i had the same problem at first .. no kidding its pretty hard to be a noob i know :( but when you have sut in ubuntu for about 2months youll know the most things :) :lol: O:) =D>

---

### Post by Tobster on 2006-09-14
Thanks Guys!  Im so happy hopeing let see if my Star Trek DVD will work!:biggrin:

---

### Post by haxer on 2006-09-14
Im sure it will but why didnt you say that you would only have to install Vlc-media player :D

---

