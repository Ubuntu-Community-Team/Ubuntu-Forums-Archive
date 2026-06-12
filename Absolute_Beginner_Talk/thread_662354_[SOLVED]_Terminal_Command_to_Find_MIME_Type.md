---
title: "[SOLVED] Terminal Command to Find MIME Type?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Gwasanaethau on 2008-01-08
As the title says, is there a terminal command I can use to find the MIME types of files? I know you can use nautilus to find it, but I need to use it for a script.

Thanks in advance!

---

### Post by blueridgedog on 2008-01-08
Your script can parse /etc/mime.types

---

### Post by Gwasanaethau on 2008-01-08
Thanks for the reply.

I'm looking more for something that will tell me the MIME type of a specific file. For argument's sake: ~/Desktop/random-file

---

### Post by blueridgedog on 2008-01-08
Well it is a short hop skip and a jump form knowing where it is to knowing the type:

```
root@ripstop:/etc# cat mime.types | grep mp3
audio/mpeg                                      mpga mpega mp2 mp3 m4a
root@ripstop:/etc# 
```

If you are in to scripting, a bash or Perl script could be hacked up to automate a bit of the above, our you could simply do the above when you wanted to look up a type.

---

### Post by Gwasanaethau on 2008-01-08
Hmm, that makes sense. But what about the files that have a different extension to the listed MIME type, or is that even possible?

For example: file.mp3 with a MIME type of image/png

---

### Post by WedgeHG on 2008-01-08
The command 'file' shows some information about the file.

```
$ file ~/Desktop/random-file
```

Also the -i option may be helpful as well.

from the man page: 
 -i, --mime
               Causes the file command to output mime type strings rather than
               the more traditional human  readable  ones.  Thus  it  may  say
               &#8216;&#8216;text/plain;  charset=us-ascii&#8217;&#8217;  rather  than &#8216;&#8216;ASCII text&#8217;&#8217;.

---

### Post by blueridgedog on 2008-01-08
> **Gwasanaethau said:**
> 
For example: file.mp3 with a MIME type of image/png

Ah.  You are talking about the holy grail, a mime type unrelated to the file name.  For that, the best I can offer you is the file command (see above).

```
root@ripstop:/home/james/audiotest# ls
convert.sh  sample.wma
root@ripstop:/home/james/audiotest# file sample.wma 
sample.wma: Microsoft ASF
root@ripstop:/home/james/audiotest# mv sample.wma sample.mp3
root@ripstop:/home/james/audiotest# file sample.mp3 
sample.mp3: Microsoft ASF
root@ripstop:/home/james/audiotest# 
```

---

### Post by Gwasanaethau on 2008-01-08
> **WedgeHG said:**
> The command 'file' shows some information about the file... not sure if that is what you are looking for or not.

```
$ file ~/Desktop/random-file
```
> **blueridgedog said:**
> Ah.  You are talking about the holy grail, a mime type unrelated to the file name.  For that, the best I can offer you is the file command (see above).

```
root@ripstop:/home/james/audiotest# ls
convert.sh  sample.wma
root@ripstop:/home/james/audiotest# file sample.wma 
sample.wma: Microsoft ASF
root@ripstop:/home/james/audiotest# mv sample.wma sample.mp3
root@ripstop:/home/james/audiotest# file sample.mp3 
sample.mp3: Microsoft ASF
root@ripstop:/home/james/audiotest# 
```
That's exactly it, thanks a mill, guys! :guitar:

---

### Post by blueridgedog on 2008-01-08
Éire go brách

---

### Post by Gwasanaethau on 2008-01-09
> **blueridgedog said:**
> Éire go brách

Go raibh maith agat! Slán!

---

