---
title: "installing software and apps"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by naknak987 on 2007-05-22
I have been trying to install wesnoth for 3 days now, I just can't get it to work. could someone tell me how to install this. I would like to start from the begining so that I know if I was doing it right or not. I'm currently running the feisty fawn with all the updates. My architecture is I686. If you need to know more, just ask. I would appreciate any and all help.

---

### Post by Ek0nomik on 2007-05-22
```
sudo aptitude install wesnoth
```

Does that not work for you?

---

### Post by naknak987 on 2007-05-22
I don't know what that is, or were it goes. I am new to ubuntu if you didn't know, this is my first time ever using linux. I just migrated from windows about a week ago.  :redface:

---

### Post by Ek0nomik on 2007-05-22
Oh, Ok!

I assumed too much, sorry.  :)

I am new to Linux as well, I have only been using it for about 4 months.

Anyways, navigate to Accessories.  (You know, similar to the M$ Start Menu button).  Then, click on Terminal.  Next, type (or copy and paste) what I wrote.  You will have to enter your password, but than you should be golden!

Let me know if it works and if you have any more questions.

---

### Post by naknak987 on 2007-05-22
well, It seems to be working now. \\:D/ thanks. I just have a couple more questions if you don't mind. Is this what you do whenever you want to install any kind of software? and I want to use my old icq im account, what program do i need and how do i set it up?  thanks.   ](*,) <----  thats what I feel like with ubuntu so-far, but that seems to be starting to change. \\:D/

---

### Post by khardbored on 2007-05-22
If you want to use ICQ just click on Applications/Internet and then click on "Gaim". It's the end-all messenger program. ICQ/Yahoo/MSN/etc etc etc.

---

### Post by Ek0nomik on 2007-05-22
> **naknak987 said:**
> well, It seems to be working now. \\:D/ thanks. I just have a couple more questions if you don't mind. Is this what you do whenever you want to install any kind of software? and I want to use my old icq im account, what program do i need and how do i set it up?  thanks.   ](*,) <----  thats what I feel like with ubuntu so-far, but that seems to be starting to change. \\:D/

I generally do that to install software, yes.

```
sudo aptitude search program.name
```

```
sudo aptitude remove program.name
```

```
sudo aptitude install program.name
```

These are all pretty useful commands.  Otherwise you can always install a program from source, but I would check out a tutorial on how to do that before you do it.  It's actually pretty easy, and you don't need to have a lot fo knowledge about what is actually happening, you can just kinda type things if you want.

If you want to use ICQ, MSN, AIM, GoogleTalk, Yahoo, or even IRC, you can use Pidgin.  (It used to be called Gaim--but AOL sued them and this is the new name)  You can compile from source, or download and install it the way we did before.

```
sudo aptitude install pidgin
```

Than it should show up in the Internet category.  

Again, if you have more questions let me know, I will subscribe to the thread and check it later tonight.  :)

---

### Post by naknak987 on 2007-05-22
Gaim, wont let me log into my old icq account and I tryed installing pidgin the way you said, but it didn't find anything. I really feel like I'm hitting a brick wall. When I search for pidgin, it doesn't turn back any results either.

---

### Post by ep2011 on 2007-05-22
> **Ek0nomik said:**
> 
```
sudo aptitude install pidgin
```

Than it should show up in the Internet category.  

Again, if you have more questions let me know, I will subscribe to the thread and check it later tonight.  :)


Pidgin is not in the respiratory yet so the only way to install is getdeb.org or from source. I'm just sticking to gaim for now.

> **naknak987 said:**
> Gaim, wont let me log into my old icq account and I tryed installing pidgin the way you said, but it didn't find anything. I really feel like I'm hitting a brick wall. When I search for pidgin, it doesn't turn back any results either.

If it "wont let you" log in, it's probably something like icq deleted your account, or something similar to that, it isn't something on gaims or ubuntus end.

---

### Post by naknak987 on 2007-05-22
then what should i do about it not letting me log into my old icq account?

I figured it out, It was a mistake on my end.  sorry.

---

### Post by DUNC4N on 2007-05-22
I don't know much about ICQ, but gaim should definately work. Make sure your number/pass is right, and you might try to reset the password, or verify on another machine that its working.


Pidgin thread here-[http://ubuntuforums.org/showthread.php?t=441363&highlight=pidgin]("http://ubuntuforums.org/showthread.php?t=441363&highlight=pidgin")

---

### Post by Ek0nomik on 2007-05-22
> **ep2011 said:**
> Pidgin is not in the respiratory yet so the only way to install is getdeb.org or from source. I'm just sticking to gaim for now.



If it "wont let you" log in, it's probably something like icq deleted your account, or something similar to that, it isn't something on gaims or ubuntus end.

You're right, sorry.

**naknak987**:  You should be able to get pidgin from [http://www.getdeb.net](http://www.getdeb.net).  Hopefully that works.  :)

---

### Post by naknak987 on 2007-05-23
Thanks guys, I have everything working now. You all were a big help. Peace and see you around.

---

