---
title: "ubuntu cannot read the swedish language. please help me"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by tuxulin on 2007-12-04
i have been using kubuntu for a good many months 
and now i have discovered now a problem.

text files created in windows with swedish language as contents.
when open into ubuntu using knotes, open office or through konqueror
they simply fails to recognize the swedish letters "ö,ä,and å" and replace them 
with "?" in a red diamond space thingy.

when i open these file in windows simple basic text pad
works just fine.

i have about 2 megs of these types of text files that i have to work with 
and i dont want to return to windows to do this.

how do i get kubuntu gusty gibbon 7.10 to open and read the swedish 
contents of a text file correctly that was created under windows ?

here is a sample output of a text file

"Vi tr&#65533;ffades som vi vanligen g&#65533;r och b&#65533;rjade visa varandra v&#65533;ra prylar, j&#65533;mf&#65533;rde, 
f&#65533;rstorade och tippade om vem som kunde spela ut vem. D&#65533; sa Mark; "varf&#65533;r g&#65533;r jag 
inte en websida d&#65533;r vi kunde s&#65533;lja v&#65533;ra prylar billigt, byta v&#65533;ra gamla prylar eller 
bara sk&#65533;nka bort gamla saker,"

Tuxulin

---

### Post by mali2297 on 2007-12-04
I have not had this problem myself, but I think **utf8-migration-tool** can convert the files into UTF-8 encoding.

```

sudo apt-get install utf8-migration-tool
utf8migrationtool

```

---

