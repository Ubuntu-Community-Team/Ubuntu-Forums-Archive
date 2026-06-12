---
title: "[offtopic]Do you Suspect anything in this image"
date: 2009-03-09
forum: Art &amp; Design
---

### Post by chrismarsh on 2009-03-09
edit

---

### Post by albandy on 2009-03-09
JFIF
 $.' ",#
(7),01444
'9=82<.342
!22222222222222222222222222222222222222222222222222
$3br
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
	#3R
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
.:0;
passlst.txt.txt
J+Eu
o/PK
.:0;
passlst.txt.txtPK

---

### Post by chrismarsh on 2009-03-09
edit

---

### Post by albandy on 2009-03-09
You need the program used to made the image

---

### Post by Rhubarb on 2009-03-09
```
rhubarb@uberrhubarb:~$ stegdetect theimage.jpg 
theimage.jpg : appended(187)<[nonrandom][Zip archive data, at least v2.0 to extract][PK..........e:..]>
```

Opening up "passlst.txt.txt" presents:-
```
I could not write the password here as it is not quite sHamall.
```

stegdetect tells me it was probably created by **camouflage** or **appendX**

I don't know much else about this.

Also running **stegbreak**'s dictionary attacks with a few different switches brings up nothing.
- it's not a big file, and the picture contains the same coloured pixels throughout.

So I don't think there's a password in this picture, unless it's the text file somehow.

---

### Post by chrismarsh on 2009-03-09
Thanks a lot for that information..When i tried to uncamouflage it is asking for a password..as it has no password It is not camouflaged actually...Now trying AppendX

---

### Post by chrismarsh on 2009-03-10
Ok got a new hint
The message you found contains the name of a technique used for encryption and encoding of data. You need to decode/decrypt the message using that..So now i have to deocde it using sha..????

---

### Post by Rhubarb on 2009-03-11
I don't know enough about SHA to know what I'm doing.
I can make it spit out a SHA1 checksum, but that'll spit out a big long hexadecimal number.

The best I can think of would be to run a simple well-know ROT13 cipher on what may be the keyword "sHamall".
This would give you a possible answer of: **fUnznyy**

The "secret" contents of a file is very often not stored with a password for that file, somewhere else in that file.

I'm not so sure (given my very brief exposure to SHA) this is encrypted with SHA - to me it looks like a simple cipher, like ROT13, or perhaps even a Caesar cipher.

It would also greatly help me if I knew more stuff about the many SHA algorithms, and it'd also be nice to know if you know how long the password is / what the password is made up of (hexadecimal / ASCII / lowercase / decimals).

And of course it'd be nice to know why you need help doing this, and perhaps more specifically, why you need to know this.

---

