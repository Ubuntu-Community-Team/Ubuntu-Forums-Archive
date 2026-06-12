---
title: "Installing fonts"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Drew555 on 2007-03-16
How do I install more fonts?

I want to install more fonts so that I have more options in Gimp.

I have no idea where to start.

Heeeeeeeeeeeeeeeelp.....

---

### Post by SishGupta on 2007-03-16
create a ".fonts" directory in your home directory and put fonts there.

---

### Post by Drew555 on 2007-03-16
That simple?

Like just download the ttf into the fonts directory and thats that?

Gimp will automatically find them and let me use them?

---

### Post by MrKlean on 2007-03-16
Here ya go ; )  This might help ya ; )

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by Perfect Storm on 2007-03-16
> **Drew555 said:**
> That simple?

Like just download the ttf into the fonts directory and thats that?

Gimp will automatically find them and let me use them?

Aye. Nothing more nothing less ;)

---

### Post by Drew555 on 2007-03-16
Thanks people, got it sorted.

Mucho thanks in fact.

---

### Post by BLTicklemonster on 2007-03-19
No way. It's that simple? So where do I get the fonts from? Just use any true type fonts I find anywhere?

---

### Post by derfinsterling on 2007-03-20
Placing them into a .files directory doesn't work for me - neither GIMP nor OpenOffice found the fonts I put there.
Do I have to check for the rights or has the file extension to be written small or big or...?

---

### Post by ferg on 2007-03-20
> **derfinsterling said:**
> .files directory
 
Try *.fonts* ;)

---

### Post by derfinsterling on 2007-03-20
Oh, I meant .fonts... don't know why I was writing .files. I blame the lack of coffee!

---

### Post by buuntuu! on 2007-03-20
read the [wiki]("https://help.ubuntu.com/community/FontInstallHowto") on installing fonts. it explains what to do if fonts don't get recognized automatically. always a good place for finding answers!

---

### Post by david_kt on 2007-03-20
> **BLTicklemonster said:**
> No way. It's that simple? So where do I get the fonts from? Just use any true type fonts I find anywhere?

Yes, you can copy all your windows'  fonts and put it in .fonts folder, and then type in terminal:

[INDENT]fc-cache -f -v[/INDENT]

DK

---

### Post by derfinsterling on 2007-03-21
Weird. I created the .fonts folder again, this time it worked.
Probably mis-typed the first time.

---

### Post by BLTicklemonster on 2007-03-21
I just installed Feisty recently, so I wanted cool fonts for gimp. I looked around, and finally decided that if all else fails, to use synaptic. I searched for font and installed a bunch, and man, there's some wild looking stuff in there to be had!


wow, .fonts works. I just downloaded a zipped ttf for windows font and extracted it there, and it's there. Way too cool. Thanks everyone!

---

### Post by Najmudin on 2007-03-23
> **david_kt said:**
> Yes, you can copy all your windows'  fonts and put it in .fonts folder, and then type in terminal:

[INDENT]fc-cache -f -v[/INDENT]

DK

I m new to ubuntu

I tried the way you mentioned here but it did not work for me , the fonts which i add to the .fonts directory dose not shown in the font viewer or in open office.
I don't know what is the problem exactly , should i do any changes to .fonts which i make , or should i do something else , or maybe i did not make the .fonts folder correctly.

Please help me :(

---

### Post by BLTicklemonster on 2007-03-23
Heck, all I did was put them in the .fonts folder and they showed up in gimp. I never noticed the command, but I just did and ran it. Here's what I got:

```
bill@bill-desktop:~$ cd /home/bill/.fonts
bill@bill-desktop:~/.fonts$ fc-cache -f -v
/usr/share/fonts: caching, 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, 1 fonts, 27 dirs
/usr/share/fonts/truetype/arphic: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/baekmuk: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/sjfonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, 23 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-devanagari-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gentium: caching, 4 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-gujarati-fonts: caching, 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kannada-fonts: caching, 8 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-larabie-deco: caching, 156 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-larabie-straight: caching, 154 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-larabie-uncommon: caching, 141 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-mgopen: caching, 16 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-oriya-fonts: caching, 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-tamil-fonts: caching, 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: caching, 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-xfree86-nonfree: caching, 12 fonts, 0 dirs
/usr/share/fonts/type1: caching, 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, 35 fonts, 0 dirs
/usr/share/X11/fonts: caching, 0 fonts, 6 dirs
/usr/share/X11/fonts/100dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/75dpi: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/Type1: caching, 8 fonts, 0 dirs
/usr/share/X11/fonts/encodings: caching, 0 fonts, 1 dirs
/usr/share/X11/fonts/encodings/large: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/misc: caching, 0 fonts, 0 dirs
/usr/share/X11/fonts/util: caching, 0 fonts, 0 dirs
/usr/local/share/fonts: caching, 0 fonts, 0 dirs
**_/home/bill/.fonts: caching, 1 fonts, 0 dirs_**
/var/lib/defoma/fontconfig.d: caching, 0 fonts, 26 dirs
/var/lib/defoma/fontconfig.d/A: caching, 14 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/B: caching, 11 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/C: caching, 12 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/D: caching, 25 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/E: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/F: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/G: caching, 16 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/H: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/I: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/J: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/K: caching, 6 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/L: caching, 18 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/M: caching, 19 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/N: caching, 23 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/O: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/P: caching, 5 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/R: caching, 3 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/S: caching, 9 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/T: caching, 18 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/U: caching, 13 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/V: caching, 5 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/W: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/a: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/j: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/m: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: caching, 1 fonts, 0 dirs
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/bill/.fontconfig: cleaning cache directory
fc-cache: succeeded
bill@bill-desktop:~/.fonts$ 


```

So it worked for me.

---

### Post by erwinquita on 2007-03-23
Here's a [[COLOR="DarkRed"]screencast[/COLOR]]("http://www.ibatayo.com/rails/categories/5/posts/51") on [[COLOR="DarkRed"]how to install fonts in ubuntu[/COLOR]]("http://www.ibatayo.com/rails/categories/5/posts/51")

copy ttf files to
/usr/share/fonts

and then rebuild your font cache with:
sudo fc-cache -f -v

Hope this helps!

---

### Post by Najmudin on 2007-03-23
Im sorry for that but i m still novice on that .
I failed to copy the fonts to ( usr/share/fonts) , there is no access to it , when i entered the properties of it, i found that the owner is ( root ) not me :confused:  . 
How can i change this or be able to copy - paste them to fonts directory.
Thanks for all

---

### Post by Perfect Storm on 2007-03-23
Use sudo.

sudo cp <option> <file> <distination>


**man cp** if you want to know which options you have with cp.

---

### Post by Najmudin on 2007-03-24
> **Artificial Intelligence said:**
> Use sudo.

sudo cp <option> <file> <distination>


**man cp** if you want to know which options you have with cp.

What i should write in <option> <file> <distination> or just copy paste them in sudo

can you explain more.

---

### Post by david_kt on 2007-03-24
> **Najmudin said:**
> Im sorry for that but i m still novice on that .
I failed to copy the fonts to ( usr/share/fonts) , there is no access to it , when i entered the properties of it, i found that the owner is ( root ) not me :confused:  . 
How can i change this or be able to copy - paste them to fonts directory.
Thanks for all

To save the trouble, just make a directory in your home folder. Open your home folderl:

[INDENT]Places>Home Folder/INDENT]

Make a .font directory:
[INDENT]File> Create Folder and name it .fonts[/INDENT]

Make the folder visible:
[INDENT]View>Show Hidden Files[/INDENT]

Copy/extract  whatever fonts you want to install in this folder.

Open terminal:
[INDENT]Applications>Accesories>Terminal[/INDENT]

copy and paste below command and enter:

[INDENT]fc-cache -f -v[/INDENT]

DK

---

### Post by Najmudin on 2007-03-24
> **david_kt said:**
> To save the trouble, just make a directory in your home folder. Open your home folderl:

[INDENT]Places>Home Folder/INDENT]

Make a .font directory:
[INDENT]File> Create Folder and name it .fonts[/INDENT]

Make the folder visible:
[INDENT]View>Show Hidden Files[/INDENT]

Copy/extract  whatever fonts you want to install in this folder.

Open terminal:
[INDENT]Applications>Accessories>Terminal[/INDENT]

copy and paste below command and enter:

[INDENT]fc-cache -f -v[/INDENT]

DK


I followed your instruction to add the fonts but something is not clear for me, there is no option with view>show Hidden Files , i selected Properties >Permissions and changed the  file access to Read & Write then i goes to Terminal using the > fc-cache -f -v and press enter
and i got this result:

[IMG]http://img109.imageshack.us/img109/2888/screenshottz0.jpg[/IMG]

It only read 58 font , but the fonts i add on the folder where around 520 fonts ???!!!:confused: 
when i came back to the fonts folder and selected Properties>Permissions i found that the change which i made was not applied , here is the result:

[IMG]http://img119.imageshack.us/img119/1672/screenshot2es2.jpg[/IMG]

Thats is my problem, sorry for my bad English

---

### Post by Perfect Storm on 2007-03-24
> **Najmudin said:**
> What i should write in <option> <file> <distination> or just copy paste them in sudo

can you explain more.

cd /where/your/fonts/are
sudo cp -r *.tff /usr/share/fonts

---

### Post by david_kt on 2007-03-25
> **Najmudin said:**
> I followed your instruction to add the fonts but something is not clear for me, there is no option with view>show Hidden Files , i selected Properties >Permissions and changed the  file access to Read & Write then i goes to Terminal using the > fc-cache -f -v and press enter
and i got this result:


View>Show hidden files is just for you to be able to see .fonts folder, which is hidden. Or, if you could not find it, just press CTRL+H, to see hidden files, so that you could open you .fonts folder. After that, make sure all your fonts is copied inside this folder.

DK

---

### Post by david_kt on 2007-03-25
Did you create "fonts" folder or ".fonts" folder in your home folder? It is important to put dot in front of fonts.

DK

---

### Post by Najmudin on 2007-03-25
> **david_kt said:**
> Did you create "fonts" folder or ".fonts" folder in your home folder? It is important to put dot in front of fonts.

DK

Oh my god finally it worked thanks allot man , really thank you so much, that was the missing point with me after two weeks of trying , its done , i cant believe it:) :) :) :)

---

### Post by tomdkat on 2007-04-15
Excellent thread!  I was about to install a bunch of Windows fonts and using the ".fonts" directory is working out perfectly!  :)

Thanks!

Peace...

---

### Post by chakkaradeep on 2007-04-17
Its strange but there is no font installer in gnome ??..newbies to linux certainly cannot use the information in this thread, they need to be provided with a tool. Is there any tool available already ?

---

### Post by airtonix on 2007-04-17
**Howto Install Fonts for All Users**

*nautilus is your font installer.*
1. click the desktop in a non icon-populated-area and then press : 
 > alt+f2

2. to load up the nautilus browser with sudo access (*so we can write into the global fonts folder*) type : 
> gksudo nautilus fonts://
if you have thumbnail previews on for file contents, each font-files thumbnail will be a preview for itself.

3. To install new fonts, drag and drop your .ttf or other font-file-types into this folder.

---

### Post by chakkaradeep on 2007-04-17
> **airtonix said:**
> **Howto Install Fonts for All Users**

*nautilus is your font installer.*
1. click the desktop in a non icon-populated-area and then press : 
 
2then type : 



This will load up the nautilus browser with sudo access...and if you have thumbnail previews on for file contents, each font-files thumbnail will be a preview for itself.

To install new fonts, drag and drop your .ttf files into this folder.

Still...something similar to what available in KDE - Fonts Installer

---

### Post by centyx on 2007-04-25
I'm trying to install some vga fonts that I have previously used with earlier versions of Ubuntu, specifically sabvga and uni-vga, and a couple of others. I have copied these to ~/.fonts/ and run 'sudo fc-cache -f -v' with no success. I also tried creating a subdirectory, ~/.fonts/vgafonts, and running mkfontdir therein, and rerunning fc-cache, but still no joy. Anyone have ideas?

Thanks!

Michael

---

