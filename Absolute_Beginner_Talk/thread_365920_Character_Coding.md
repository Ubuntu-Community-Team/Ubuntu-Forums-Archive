---
title: "Character Coding"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by LKN4SPACE on 2007-02-20
HI, I'm a total NOOB. I just installed Ubuntu yesterday but i am having character coding problems when i try to install a program. I get:

Could not open the file /home/denny/Downloads/in…er-standard-demo-6.0.0.sh.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
 (Current Locale (UTF-8)

I tried other character codings but they don't work. What do i do now??

Thank you!

---

### Post by chggr on 2007-02-22
The file ends at .sh which means that it is a shell script.
If you want to run it you should first add the permission execute to it using this command

chmod +x <file>

If you simply want to read the contents of the file, you can give it an html extension and open it using firefox. That's what I do with documents written in other caracter codings.

---

### Post by dorcssa on 2007-03-06
So, I thought this would be a good topic for my problem. I translate subtitles(with ksubtitle and gnome-subtitle), and have a little character coding problem. The default is unicode, but it looks weird in windows, so I save them in central europe iso-xxxx. But after that, when I open them with the knew character coding, some letter just can't display correctly, only &#337; and &#369;. I don't want to correct the whole sub, and it's annoying. When I dowload a subtitle(and I suppose it's western coding, coz everyone use windows), there's no problem, but &#337; and &#369; looks different, they look õ and û. They're different, but I can see what are they really, and it's better than ?Q!, or something like this. I reckon not so many people have this kind of problem, coz these are special hungarian letters...

---

### Post by dorcssa on 2007-06-05
Bump!

And the problem is more spreaded now. In the new version of gnome subtitle (0.5.1), I have problem with all the iso-8859 characters when I want to save the sub in central european, or western, or something like that encoding. These characters are: á, é, í, &#337;, &#369;. When I save the sub, and open it in the new encoding, these characters change into some chinese characters, and some consonant is dissapeared too, next to the problematic character. I tried to change the encoding in ksubtile, with cp-1252 only &#337; and &#369; stayed problematic, but only in windows, in feisty, I saw question marks instead of á, é, í &#337; and &#369;. This is a big problem for me, cos we use these characters quite often, same like a, or e.

---

### Post by noup on 2007-06-08
> **dorcssa said:**
> Bump!

And the problem is more spreaded now. In the new version of gnome subtitle (0.5.1), I have problem with all the iso-8859 characters when I want to save the sub in central european, or western, or something like that encoding. These characters are: á, é, í, &#337;, &#369;. When I save the sub, and open it in the new encoding, these characters change into some chinese characters, and some consonant is dissapeared too, next to the problematic character. I tried to change the encoding in ksubtile, with cp-1252 only &#337; and &#369; stayed problematic, but only in windows, in feisty, I saw question marks instead of á, é, í &#337; and &#369;. This is a big problem for me, cos we use these characters quite often, same like a, or e.
Character codings are usually a hard thing to deal with, as there is no way to perfectly autodetect them (except  for Unicode, which may use a specific mark on the file). That said, in Gnome Subtitles you have an option to choose the encoding, in the Open dialog, instead of auto-detection. Have you tried that?

---

### Post by dorcssa on 2007-06-09
Now that you mentioned...yes, but it's no use. And it doesn't solve the problem that in windows, you have to correct all the &#337; and &#369; characters.

---

### Post by noup on 2007-06-09
> **dorcssa said:**
> Now that you mentioned...yes, but it's no use. And it doesn't solve the problem that in windows, you have to correct all the &#337; and &#369; characters.
Could you elaborate on that? It always depends on the support for the character coding in Windows. If you save a file in UTF-8 and open it in a UTF-8 compliant application in Windows, it should work. The same way, if you use one of the ISO-8859-X encodings, you have to make sure it's supported in WIndows. Which Windows application are you using?

---

### Post by dorcssa on 2007-06-10
Subtitle Workshop, I think(my friend use it).

---

### Post by noup on 2007-06-11
> **dorcssa said:**
> Subtitle Workshop, I think(my friend use it).
IIRC Subtitle Workshop allows to select the encoding of the input file, so your friend should try that (it's in a vertical bar to the left of the application). Unlike Gnome Subtitles, it doesn't have encoding auto-detection. Though, I had the idea that if you used the system's default encoding it should work - you just have to figure out which it is (Western countries use Windows-1252, in Hungary it might be Windows-1250; you can select these when Saving As in Gnome Subtitles).

---

### Post by dorcssa on 2007-06-16
When I choose Win-1250(it's the correct I think, it was worked before), all the caracters, that has accent, change into chinese caracters, when I open the reencoded cub with gnome-subtitles. Only the mentioned encoding(iso-8859-2) works almost well, only &#337; and &#369; is a problem. And not only in the sub editor, Sub Workshop, but when you watch it with a video in example bs player.

---

### Post by noup on 2007-06-17
dorcssa, 

The problem is in the encoding detection. As I've said, it's impossible to have a 100% certain detection. When you save the file as Windows-1250 it's most certainly being saved corrected. The problem is to ensure that, when you open that file, that encoding will be used. If an application has automatic detection, and it fails, you have to manually specify the encoding. So the problem is never on saving, but instead on reading.

If you run Gnome Subtitles from a terminal, it will show the detected encodings, and the one that was selected. Can you post that information here? Still, remember that if you want BS Player to play a specific encoding, you have to specify it. Either that, or use UTF-8. Most applications (if well built) should automatically detect UTF-8 files.

> **dorcssa said:**
> When I choose Win-1250(it's the correct I think, it was worked before), all the caracters, that has accent, change into chinese caracters, when I open the reencoded cub with gnome-subtitles. Only the mentioned encoding(iso-8859-2) works almost well, only &#337; and &#369; is a problem. And not only in the sub editor, Sub Workshop, but when you watch it with a video in example bs player.

---

### Post by dorcssa on 2007-06-22
It doesn't matter now...I don't know how, but it's just works now, with cp-1252 coding. :)

---

