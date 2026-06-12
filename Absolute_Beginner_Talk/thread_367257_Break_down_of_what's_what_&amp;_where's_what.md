---
title: "Break down of what's what &amp; where's what"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by raggit on 2007-02-21
ok, this has always baffled the hell out of me and I need some clarification to resolve this.

In windows, you can goto C:/Program Files/whatever app you want, and find the executable for that particular program immediately after installing the program.  Well here's the thing, I found myself today looking for the executable for evolution, or hell any program for that matter.  Where are they, why are they there and are they all located in a neat organized way such as program files?  If you entertain an answer here please make it as if you are speaking to a 3rd grader.

Thanks

---

### Post by poohbear1616 on 2007-02-21
This link gives you some idea.

[http://www.linuxcommand.org/lts0040.php]("http://www.linuxcommand.org/lts0040.php")

---

### Post by aysiu on 2007-02-21
Try:
/usr/bin

Also, check out:
[http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go)

---

### Post by mikewhatever on 2007-02-21
Hi,
I am no expert and may be wrong, but the following three commands seem to be the easiest way to find applications:
>  which evolution

whereis evolution

locate evolution


It seem that the first command finds an executable. If you want to know more on what they do, type 'man command' in the terminal. For example 'man which' will output a lengthy manual on which. I found those three surprisingly useful compared to the search function in nautilus.

---

