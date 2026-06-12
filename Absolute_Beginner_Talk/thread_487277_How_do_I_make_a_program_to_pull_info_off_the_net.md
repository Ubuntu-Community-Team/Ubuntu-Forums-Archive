---
title: "How do I make a program to pull info off the net"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-06-28
I want to make a karamba widget to pull some info off the website [jhfunds.com]("http://www.jhfunds.com/"). But as far as I can tell the only way to do this is to learn python. I tried to wget the page and pull info off of it that way using python (f.read command) but all I got was the pages source code (off of my downloaded html file). Am I going about this the wrong way or am I compleatly lost and need to dive in to some programing before I try to tackle this. Also I think I might need an API for that website? (I'm not entirely sure what an API is) Thanks for any inputs.

---

### Post by jfinkels on 2007-06-29
> **thelocust said:**
> I want to make a karamba widget to pull some info off the website [jhfunds.com]("http://www.jhfunds.com/"). But as far as I can tell the only way to do this is to learn python. I tried to wget the page and pull info off of it that way using python (f.read command) but all I got was the pages source code (off of my downloaded html file). Am I going about this the wrong way or am I compleatly lost and need to dive in to some programing before I try to tackle this. Also I think I might need an API for that website? (I'm not entirely sure what an API is) Thanks for any inputs.

Python has modules for downloading pages from (and doing other stuff with) the internet, take a look at urllib2: [http://docs.python.org/lib/urllib2-examples.html](http://docs.python.org/lib/urllib2-examples.html)

When you grab a webpage from the internet (like when you did it with Python) you are grabbing the entire HTML source of that page. You are just downloading the file from whatever server it lives on, and the file consists of HTML (like when you choose "View Source" in your web browser). If you want just some of the information, you'll have to sort through all the HTML tags and other stuff that you don't want to cut out extraneous data.

It is true that there are some websites (like Amazon.com, for example) that offer an API (an Application Programming Interface). An API consists of functions, classes, methods, etc. which allow for a simpler interface to gathering information from, in this case, the website, but it could be from any source.

For example, let's say there were an API for jhfunds. You might be able to import it into your python program, and call "getAccountHolder()" or something like that to get the name of the holder of a certain account. Unfortunately, I doubt John Hancock wants to give any old user access to information about accounts and important stuff like that.

What are you trying to do exactly?

---

### Post by phr0ze on 2007-06-29
Is this really considered an Absolute Beginner topic?

---

