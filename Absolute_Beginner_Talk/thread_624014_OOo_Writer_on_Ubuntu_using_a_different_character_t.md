---
title: "OOo Writer on Ubuntu using a different character to mark end of paragraph"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-11-26
I load files that I've created with a DOS application that produces only ascii text files into OpenOffice Writer to check spelling and format for printing. Previously I'd been doing this on my Windows system because I hadn't yet installed the DOS application on my Ubuntu system. 

Yesterday I figured out how to run the DOS app in DOSbox. When I loaded the files I'd created with it into Writer for spellchecking and then saved them as text files, I found that Writer is using a character to mark the end of the paragraph that my DOS app doesn't recognize as an end of paragraph. [In the DOS app the character appears as two highlighted lower-case "o"s.]

Writer on Windows doesn't do this. Kwrite doesn't do it. I'm assuming that whoever put together Ubuntu's version of Writer is responsible. [1] Why did they do it? [2] Is there a way I can change what Writer uses to mark the end of a paragraph?

Thanks in advance,

---

### Post by Eric Weir on 2007-11-26
> **Eric Weir said:**
> I'm assuming that whoever put together Ubuntu's version of Writer is responsible. [1] Why did they do it? [2] Is there a way I can change what Writer uses to mark the end of a paragraph?

I figured this out for myself. The answer to [1] is, it's the difference between unix and dos. Unix/linux uses a LF for end-of-line. DOS uses CR/LF. In Ubuntu, Write is a Linux application, and uses the unix convention. 

The answer to [2] is, yes, and it's very simple. Write for Ubuntu has an "encoded txt" save option, where "encoded" means "encoded for DOS." If you import a DOS file, if you go to save it as a txt file Write will suggest "encoded txt." 

I'm glad it's turned out to be so simple. I was concerned that my "ecology" of MaxThink and Write was going to be disturbed.

---

