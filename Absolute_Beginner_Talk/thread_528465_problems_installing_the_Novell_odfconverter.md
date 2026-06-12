---
title: "problems installing the Novell odfconverter"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-08-17
Hello:

I am trying to install the Novell's odfconverter in Open Office. This is a application that is suppose to let you converter Microsoft 2007 Office docx files into a format that Open Office can open. I have Ubuntu 6.10, but I upgraded the open office from 2.0.2 to 2.2. 

I tried following the instructions at this forum about installing the Novell odfconventer.

[http://ubuntuforums.org/showthread.php?t=507898&highlight=2007+word+in+open+office](http://ubuntuforums.org/showthread.php?t=507898&highlight=2007+word+in+open+office)

I have downloaded and installed the package from Novell, but when it comes to copy the files from one folder to another I get this message

cp: target `/usr/lib/openoffice/program/' is not a directory: No such file or directory

So I'm not sure what to do next. I think the problem might be upgrade from 2.0.2 to 2.2

I hope that all made sense. Any help would be appreciated. This is really bugging me, because the company I work for installed Microsoft Office 2007 on all our computers at work, and half the time I forget to save my documents in an old version of word. So I can't work on them at home.

---

### Post by orwellus on 2007-08-19
I am replying to my own post. I switched back to the Open Office that came with Ubuntu 6.10 (by reinstalling Ubuntu 6.10), and got the converter to work that way. I guess if you upgrade to Open Office to 2.2, then you loss a file that the Novell converter needs. I did install Java Runtime, though, and that made the old Open Office go faster. So, in the end, some good came out of switching back. I am now closing out this post.

---

### Post by Hagar Delest on 2007-08-20
In fact, the Ubuntu version of OOo is based on the Novell build. Therefore, it has some features and compatibility with the Novell's add-ons. The official build has problems it seems with this add-on. The code must be different somewhere.

---

### Post by orwellus on 2007-08-20
Glad I checked on this post. Thank you for your reply. That makes sense. I knew that Novell had something to do with the Open Office in SUSE linux, but did not realize it applied to Ubuntu Open Office as well. Trying to get the Novell converter to work, turned out to be a happy accident, as I thought to install Java Runtime. Now Ubuntu Open Office loads as fast (perhaps faster) than Abiword. And I got the Novell converter to work as well. All because I'm using the Open Office that came with Ubuntu.

---

### Post by Hagar Delest on 2007-08-20
The problem is that the Ubuntu version is not so stable (many bugs, especially with Impress and the Base wizards). Many users have to remove it and install the official version.

But if it works fine for you, just keep it that way !

---

### Post by javroch on 2008-03-30
I'm not exactly sure why nobody else seems to have tried this, but if you download the odf-converter-x.x-x.oxt file from Novell's website, instead of the rpm, you can install it just as you would in Windows. AND, it will not only allow you to use .docx files it'll also do .xlsx and .pptx files as well. I'll outline the steps for you if you'd like:

Go to Applications > Office and open OpenOffice.org Word Processor
In OpenOffice.org Word Processor go to Tools > Extension Manager...
In Extension Manager click "Add..." and locate the .oxt file.

That's it!

---

