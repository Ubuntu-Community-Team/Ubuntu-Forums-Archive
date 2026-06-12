---
title: "Script or a program to monitor website updates"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bbukh on 2007-10-04
I would like to be informed when a certain (infrequently updated) websites get updated. I would like to integrate it into my system of scripts, that I have to remind me about things I need to do (basically it is a combination of "cron", "curl" and "remind", and some simple text-parsing scripts).

What I need:
A command-line program (or a script) that can query a website over HTTP, parse Last-Modified header, compare it to the stored value, and in case it differs emit a text to stdout or a text-file.  A bonus would be if it could do something intelligent in the absence of Last-Modified header (which the http server might not provide after all).

I already know about "Specto". I specifically want a command-line program that I can use inside a script.

Please, do not suggest downloading the website using wget and then diff'ing it with a local copy. It works, but since I am going to run it regularly through cron, and the number of sites is going to be large, this is a wrong solution to the problem.

Thank you for any suggestions.

Boris

---

### Post by samschoice on 2007-10-04
I use Specto to monitor website updates.

---

### Post by bbukh on 2007-10-04
samschoice, did you read what I wrote?  I know about Specto, and it is not what I want for the reasons I explained. I will still appreciate any suggestions.

--Boris

---

### Post by llamakc on 2007-10-04
> **bbukh said:**
> samschoice, did you read what I wrote?  I know about Specto, and it is not what I want for the reasons I explained. I will still appreciate any suggestions.

--Boris

Be easier if you gave more details. What site are you wanting to watch, or an example of the type of site that you want to watch.

---

### Post by Maxtorm on 2007-10-05
> **bbukh said:**
> What I need:
A command-line program (or a script) that can query a website over HTTP, parse Last-Modified header, compare it to the stored value, and in case it differs emit a text to stdout or a text-file.  A bonus would be if it could do something intelligent in the absence of Last-Modified header (which the http server might not provide after all).
I'd say you're on the right track. Curl has a --dump-header option that you can use to pipe the HTTP headers to a file. You could then use sed to pull the Last-Modified field from it and compare to the previous value. However, I'm not sure how to make curl *only* pull the header. You can give it a --range parameter, but I can't get it to work as intended (i.e. tell it to only get 0 or 1 bytes). Incidentally, wget has a similar parameter (-S). Again though, there doesn't appear to be a way to tell it to get the header only.

---

### Post by hyper_ch on 2007-10-05
I'd use this approach (monitoring domain.com):

(1) create a file domain.com.txt
(2) use wget to download the page and calculate the md5 checksum
(3) compare the checksum with the one stored in the doamin.com.txt file
(4) store the new checksum in the domain.com.txt file
[(5) if the checksum is not identical, make your alert]

I wouldn't use the last modified header... that's not reliable I tend to think. Analyzing the content with a md5 checksum should be accurate.

---

### Post by bbukh on 2007-10-06
Maxtorm, thank you for trying to get wget or curl to do that.  I also could not get them to fetch only the header.

hyper_ch, I think I will use your suggestion if I cannot find anything better to do. 

--Boris

---

### Post by Maxtorm on 2007-10-06
> **bbukh said:**
> Maxtorm, thank you for trying to get wget or curl to do that.  I also could not get them to fetch only the header.
I don't know how I missed this yesterday, but it appears that curl **does** have a "headers only" option: -I (that's a capital i). Try that.

---

### Post by bbukh on 2007-10-06
> **Maxtorm said:**
> I don't know how I missed this yesterday, but it appears that curl **does** have a "headers only" option: -I (that's a capital i). Try that.

Thanks!   I also found that wget has this functionality. The option is called --spider, according to the documentation it "checks existence of a file", but when combined with "-S" it effectively just requests and prints out the header.

I apologize profusely for asking a question for which the documentation has an answer to. Thanks to everyone who helped.

--Boris

---

### Post by G|N| on 2007-12-07
I don't know if you still need it, but my development branch from specto is now able to run specto in the console.

It can be downloaded from: [https://code.launchpad.net/~woutc/specto/specto-woutc](https://code.launchpad.net/~woutc/specto/specto-woutc)
But it is still in development and may contain some bugs.

Give it a try if you want and report what you would like to see improved/changed :)

---

