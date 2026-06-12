---
title: "Cannot figure this out. Codecs and rythmbox."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Tubob on 2007-12-20
I know what I have to do to make this work. All I want to do is import my MP3's into Rythmbox and use it.

There is something wrong with my repositories or something and I am stuck at the point in the instructions right before I install the codecs.

Any ideas?

---

### Post by Tux.Ice on 2007-12-20
have you installed your speaker codecs?

---

### Post by iris-n on 2007-12-20
Well, exactly which errors are you getting?

Can you hear other music formats (ogg, wav)?

If the problem is with your repositories, type cat /ect/apt/sources.list in the terminal and paste here the results so we can help you.

---

### Post by dcj65 on 2007-12-20
I was having problems also and while reading the post I found one of the members had his own website, I went to his website and followed his instructions and low and behold my Ubuntu works Great, The website is [www.stchman.com](www.stchman.com)

Hope this helps

---

### Post by Tubob on 2007-12-21
cat: /ect/apt/sources.list: No such file or directory

I take it that this makes me look really stupid.

---

### Post by atomkarinca on 2007-12-21
That should be:

```
gksudo gedit /etc/apt/sources.list
```

It's just a typo, no big deal :)

---

### Post by Tubob on 2007-12-21
Nevermind, I got a little help from a friend and I'm all good. Thanks for the help.

---

