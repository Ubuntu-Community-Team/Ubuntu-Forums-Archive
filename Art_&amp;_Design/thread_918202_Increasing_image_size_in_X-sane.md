---
title: "Increasing image size in X-sane"
date: 2008-09-12
forum: Art &amp; Design
---

### Post by scarab on 2008-09-12
Hi!
I need to scan an image in x-sane in more than 100% of it actual size on  given resolution. My scanner is an HP Deskjet F4180 (all-in-one) Do someone knows how to do this?

(I was doing this scanning in a res higher than the needed then resizng and lowering res in post processing, but final image was not good enough.) 

thanks in advance, 

f

---

### Post by AJB2K3 on 2008-09-14
Going to sound stupid but,
Change the resolution and size in the dialogues !
You aether haven't got the front end working or you haven't got the needed dialogue open yet.

---

### Post by scarab on 2008-09-14
Resolution, OK, but size, I simply cannot see where to change it (image size, in %) in the dialogs.... where to do so? which dialog?

thanks in advance

F 


> **AJB2K3 said:**
> Going to sound stupid but,
Change the resolution and size in the dialogues !
You aether haven't got the front end working or you haven't got the needed dialogue open yet.

---

### Post by liyanricaoqiyue1314 on 2008-09-15
[size=2]Nude-calendar 1177, human and Shouzu the third "Battle of Lawson," Lawson barriers on the ground before the start of the Gap. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)This is a historic campaign, the campaign is "human beast seven years of war" in the first three major campaigns, the history of bare-called "people's car used to launch the war." [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Because, the bare-three million migrant workers has made in a month-20,000 warships, and timely expansion to the navy,[Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) so that mankind has made the absolute superiority in the sea, with both sides of the back to. And the barren Shouzufengru the mainland until the 37th of the people of God the outbreak of war. [runescape shop](http://www.runescape-shop.com/)And it is precisely because of this campaign, the first time in the bare-war history, referred to the "Portland Ruo-yun," the name, many historians experts to the expansion of the war of special significance. Some people even said that, if not the war, as there will be a great hero was inspired by, of course, will be impossible for a human return to the mainland seven glorious history. [age of conan power leveling](http://www.aoc-power-leveling.org)Moreover, we said to this great man, in this war also made a bit of good results? [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)Portland Ruo-yun from Lawson on the Fort Fangyanwangqu, with both sides of the narrow ground to beat the Shouzu row over the army. [aoc power leveling](http://www.aoc-power-leveling.org)A tall face of ferocious ethnic people Zhengning the claws, but the body is more moderate and flexible people who foot, body, wrapped in a layer of black scales in the long tentacles of the Long Tuzhuo ethnic people. Of course, the master control of the air wing wizard and although their number less, but also with the team in the final, when prone radio ready siege of human soldiers guarding the wall. [/size][size=2][buy age of conan power leveling](http://www.aoc-power-leveling.org)Mankind's troops began to open Lawson barriers, 200,000 of the green collar Tieqi, hidden in two wings of the Tieqi second only to God bow of the 50,000 camp bow riders, and are in the final of the 300,000 Yazhen infantry. [buy aoc power leveling](http://www.aoc-power-leveling.org)Interval between the two sides about two kilometers distance from each other to see the other side of the bright banner of omnipresent there shaking. Ma Si Ming and the anger of the arms occasionally break out the [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)sound of the collision, but the two sides is almost non-soldiers heard voices, the silence before the war that is reinforced by the kind of Qishixiongxiong Fengyuyulai. [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)The weather has also Laicourenao this time, to beat the dark clouds gradually from the [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) floating over the horizon, live coverage of the original is also clear skies, Yuan Yidian gradually so that the soldiers almost clear of each other's faces, the temperature suddenly dropped. So many people and irritable, even more tense over the past fainted. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)Line-up finish. Last night talk election effort a silvery white armor, general Pigua&#24471;&#19981;skin to stay one point, struggling carrying a spear, at the moment Lawson body trembling from the Fort-Ruo-yun, although aware that this time only The first student, is not played with, but on the battlefield or Sheyu powerful Shaqi, the lack of tension in the Tuiruan body. [/size]

---

### Post by unutbu on 2008-09-15
scarab, are you trying to print out the scanned image?
If so, when you print, is there an option to change the DPI (dots-per-inch)?

---

### Post by scarab on 2008-09-15
it is not for me for printing.

I need to send images to another person in a given size and resolution (in tiff)...

but originals are smaller than the needed size. 

scanning via Windows, using the original scanner's interface, I can scan something of 3x4in to 15x20in in 300 DPI, for instance. but I cannt find in xsane a dialog to do so...

I already tried (in linux) to scan it in a higher resolution, then paste to inkscape, then export it in a given size, but the final artwork is not so good as if I had directly generated the scanned image in the given size and resolution I need. No, I do not unsderstand exactly why it does not work, but anyway, it is a longer way, and I would really appreciate to be able to do all directly in xsane...

any ideas are welcome!

---

### Post by unutbu on 2008-09-15
[list]
[*]What is the size of the original
[*]What is the desired size of the output
[*]What is the DPI of your scanner
[*]What is the DPI of the printer, or what is the desired resolution that you need to send to the printer?
[/list]

Your Windows program may have been able to resize the data before outputting it to a tiff file, but it may be the case that xsane does not have that functionality built-in. I am not familiar with xsane, but I took a look at the documentation at [http://www.xsane.org/doc/sane-xsane-doc.html](http://www.xsane.org/doc/sane-xsane-doc.html) and could not find any option to resize the data. 

It might be necessary to use a separate tool to do the resizing.
Inkscape is for scalable vector graphics. I doubt it would be the best tool for scaling bitmaps such as your tiff. 

Perhaps try GIMP, or imagemagick.

To resize using imagemagick, see 
[http://ubuntuforums.org/showpost.php?p=5790627&postcount=7](http://ubuntuforums.org/showpost.php?p=5790627&postcount=7)

---

### Post by lharb704 on 2009-01-31
I know this post is a few months old, but thought somebody else might benefit from it as well.  I believe the OP is referring to the output image resolution.  It took me a little while to figure it out too.

In xsane, you can alter this by going to the main xsane window, clicking View and making sure "show resolution list" is checked.  Having that checked will show an option about midway in the middle of the window that has a number in it, defaults to 50, I think.  This is the scan DPI.  You can bump this up a bit and the apparent output resolution will increase the next time you scan something. 

> **scarab said:**
> Resolution, OK, but size, I simply cannot see where to change it (image size, in %) in the dialogs.... where to do so? which dialog?

thanks in advance

F

---

