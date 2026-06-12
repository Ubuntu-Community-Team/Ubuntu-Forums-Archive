---
title: "Urgent: How do I get Hindi (Devnagri script) to show in OpenOffice Writer?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-02-15
How do I get Devnagri (that's the script for Hindi) characters to show up in OpenOffice Writer?
Thanks.

---

### Post by kpkeerthi on 2008-02-15
I assume it is a TTF font. Just drop the file to $HOME/.fonts (Create this folder if it doesn't exist). Open a terminal and type
```

fc-cache -fv

```

Should be listed on OO writer now.

---

### Post by kleo skywalker on 2008-02-15
> **kpkeerthi said:**
> I assume it is a TTF font. Just drop the file to $HOME/.fonts (Create this folder if it doesn't exist). Open a terminal and type
```

fc-cache -fv

```

Should be listed on OO writer now.

I'm not really sure I get what you mean. What file should I drop into the folder?
Also, since you mention TTF fonts, I have the package **ttf-devanagri-fonts** installed in Synaptic.

---

### Post by kpkeerthi on 2008-02-15
So you installed the ubuntu package. Then the TTF files should have been already copied to /usr/share/fonts folder. You need to refresh the font cache using the command I gave in my last post and check if the fonts are listed on Oo.

---

### Post by kleo skywalker on 2008-02-15
> **kpkeerthi said:**
> So you installed the ubuntu package. Then the TTF files should have been already copied to /usr/share/fonts folder. You need to refresh the font cache using the command I gave in my last post and check if the fonts are listed on Oo.

I ran that command, and the Devnagri letters still show up as gibberish.
And what fonts am I supposed to look for?

---

### Post by acidsolution on 2008-02-15
try to download some font manually for devnagiri and than try to 
i.e copy the font.ttf to /home/user/.fonts folder, if .fonts folder doesnot exist in your home directory than create it 
after that type command fc-cache -fv

now restart you open office it should do for you 
note: if you are opening some existed document which is in devganiri font than you shuld make sure that the font use in document is the same one as you are installing.
other devnagiri font may not necessary do ..
I have followed this process and i got devganiri font working on mine openoffice

---

### Post by kleo skywalker on 2008-02-15
> **acidsolution said:**
> try to download some font manually for devnagiri and than try to 
i.e copy the font.ttf to /home/user/.fonts folder, if .fonts folder doesnot exist in your home directory than create it 
after that type command fc-cache -fv

now restart you open office it should do for you 
note: if you are opening some existed document which is in devganiri font than you shuld make sure that the font use in document is the same one as you are installing.
other devnagiri font may not necessary do ..
I have followed this process and i got devganiri font working on mine openoffice

Ok, I'll try that too, but what font should I download and where from?

---

### Post by kleo skywalker on 2008-02-16
bump

---

### Post by peabody on 2008-02-16
I would look in the synaptic package manager.  Look at all packages starting with ttf-.  Those are all of the truetype fonts for all the different international languages out there.  From my understanding most are installed per default, but it could be your language isn't.  Worst case scenario is that it may not be available in which case you'll follow other people's advice on this thread of searching the internet for a devnagri ttf font.

---

### Post by kleo skywalker on 2008-02-16
> **peabody said:**
> I would look in the synaptic package manager.  Look at all packages starting with ttf-.  Those are all of the truetype fonts for all the different international languages out there.  From my understanding most are installed per default, but it could be your language isn't.  Worst case scenario is that it may not be available in which case you'll follow other people's advice on this thread of searching the internet for a devnagri ttf font.

Like I posted before, I already have the **ttf-devanagri-fonts** package installed in Synaptic.

---

### Post by peabody on 2008-02-16
> **kleo skywalker said:**
> Like I posted before, I already have the **ttf-devanagri-fonts** package installed in Synaptic.

So, to clarify...are you able to get that script in other applications?  Is it an OO specific problem?

---

### Post by kleo skywalker on 2008-02-17
> **peabody said:**
> So, to clarify...are you able to get that script in other applications?  Is it an OO specific problem?

Er... I don't need the script in other applications, so I haven't tried.
It's a .doc file with parts in Devanagri script, and that shows up as gibberish when I open it with OpenOffice Writer.

---

### Post by peabody on 2008-02-17
Is there anyway you could test if it was OOo specific.

---

### Post by kleo skywalker on 2008-02-18
> **peabody said:**
> Is there anyway you could test if it was OOo specific.

How would I do that? I don't know another word processor that supports the language.
A person with MS Word can see the Devnagri characters alright (I know because they emailed it to me in the first place) - does that count?

---

### Post by housam on 2008-02-18
Hi every one , this is a small guide to install and use any language on your machines :

If you can connect the Internet through the live cd , do sys>> admin. >> language support .it'll download / install the language package.

If not , boot normally and connect to the Internet and then do sys. >> admin. >> software sources . this will download the univers and the multivers packages. then do sys>> admin. >> language support . this will download the required language among other languages. tick the square in front of it to start installing .

after that go for the upper panel and right click >> add to panel >> utilities >> keyboard indicator.>> add.

after that you will find a word 'USA' appears on the panel. right click on it >> keyboard preference >> layouts >> add >> your language.
this will ease the switch between languages during writing.

Good luck
__________________

---

### Post by acidsolution on 2008-02-18
You can download fonts from here 
[http://envfor.nic.in/hindi/fonts/download.html](http://envfor.nic.in/hindi/fonts/download.html) download .zip for manual extraction
or you can get many other site just google it and than try ..

---

### Post by Tyke91 on 2008-02-18
I think your problem comes from someone using MS word to send you this message instead of OpenOffice. Word's Devnagri font might be alot different than Open Office's.

---

### Post by kleo skywalker on 2008-02-18
> **Tyke91 said:**
> I think your problem comes from someone using MS word to send you this message instead of OpenOffice. Word's Devnagri font might be alot different than Open Office's.

That might very well be the reason, but I still need to get it working!

---

### Post by kleo skywalker on 2008-02-18
> **housam said:**
> Hi every one , this is a small guide to install and use any language on your machines :

If you can connect the Internet through the live cd , do sys>> admin. >> language support .it'll download / install the language package.

If not , boot normally and connect to the Internet and then do sys. >> admin. >> software sources . this will download the univers and the multivers packages. then do sys>> admin. >> language support . this will download the required language among other languages. tick the square in front of it to start installing .

after that go for the upper panel and right click >> add to panel >> utilities >> keyboard indicator.>> add.

after that you will find a word 'USA' appears on the panel. right click on it >> keyboard preference >> layouts >> add >> your language.
this will ease the switch between languages during writing.

Good luck
__________________
 
I tried this, and I can type in Hindi (Devnagri script) in new documents, but the Devnagri characters in that original file - the one I'm trying to see -  are still jumbled.

---

### Post by kleo skywalker on 2008-02-18
I even asked the person who sent me the file for the font they used. I downloaded it, and followed kpkeerthi's instructions - save in my home in .fonts, then run ```
fc-cache -fv
```

The font shows up in OO and works ok when I use it to type text in a file. BUT when I select the jumbled text and change the font to this new one, the script changes from roman to devnagri, but it's still nonsense.
I'm clueless.

---

### Post by peabody on 2008-02-18
My guess is that it's not a font issue but an encoding issue.

I know this isn't the solution you're looking for, but seeing as how OOo is free, is there any chance your friend could download it to his machine and try and open the document on his machine with OOo?  May then he could see about saving it as an odt and seeing if you have better luck with that format?

---

### Post by kleo skywalker on 2008-02-19
> **peabody said:**
> My guess is that it's not a font issue but an encoding issue.

I know this isn't the solution you're looking for, but seeing as how OOo is free, is there any chance your friend could download it to his machine and try and open the document on his machine with OOo?  May then he could see about saving it as an odt and seeing if you have better luck with that format?

I can't, it's work-related. (I can't possibly ask a company to use OO just because I use it and can't see the letters!)

---

### Post by peabody on 2008-02-19
> **kleo skywalker said:**
> I can't, it's work-related. (I can't possibly ask a company to use OO just because I use it and can't see the letters!)

If it's that important you should probably keep a windows machine around for work, or get Word to work through wine or crossover office.  I'm all for keeping things on free software, but you gotta do what you gotta do you know?

---

### Post by kleo skywalker on 2008-02-20
> **peabody said:**
> If it's that important you should probably keep a windows machine around for work, or get Word to work through wine or crossover office.  I'm all for keeping things on free software, but you gotta do what you gotta do you know?

I really want to get it to work in OO, having  a Windows machine is not really an option for me.

---

### Post by bw44 on 2008-03-05
> **kleo skywalker said:**
> I really want to get it to work in OO, having  a Windows machine is not really an option for me.Have you had any luck with this problem?

I'm far from an expert on fonts, but I used the $ fc-cache -fv command to install a set of custom fonts in Ubuntu that I had previously used in MS Word.  I just copied them (the .ttf files)  into the /home/user/.fonts directory and ran the above command.  Then, when I imported my Word document to OpenOffice, the letters which displayed garbled before were correct.  (Before installing the Windows fonts I think OO just substituted a default font,  though it showed the correct font **name** from the Word doc in the little window in the upper left of the OO writer screen.)  When you select some good text and then some garbled text in your document, does the same font name appear in the in little window in the upper left?

What I am wondering is if the font you installed with Synaptic is really the same font that was used in your original (Windows) document.  They may both have been Devanagri, but I doubt that MS Word was using the ttf-devanagri-fonts, which are for Unix. 

I don't know if all fonts  installed under Windows can be imported to Linux (probably not), but if you can get a copy of the Devanagri .ttf file(s) from the system where you were using Word, you could try importing them.

Hope this helps.

---

### Post by kleo skywalker on 2008-03-06
> **bw44 said:**
> Have you had any luck with this problem?

No. The problem persists, but the need to solve it doesn't. 
I don't need to get it working anymore, though I may in the future. If that happens, I'll try what you suggested.
Thanks.

---

### Post by bw44 on 2008-03-06
> **kleo skywalker said:**
> No. The problem persists, but the need to solve it doesn't. 
I don't need to get it working anymore, though I may in the future. If that happens, I'll try what you suggested.
Thanks.Yes, the urgency of all problems varies.  Good luck with it, if the need again arises!

---

### Post by kleo skywalker on 2008-03-06
> **bw44 said:**
> Yes, the urgency of all problems varies.  Good luck with it, if the need again arises!

It *was* very urgent when I posted (I was to work on something like that the next day) but then the work didn't materialize so there.
Thanks for your help!

---

