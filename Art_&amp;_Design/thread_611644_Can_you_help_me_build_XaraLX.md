---
title: "Can you help me build XaraLX?"
date: 2007-11-13
forum: Art &amp; Design
---

### Post by Unterseeboot_234 on 2007-11-13
I know, I know, for Gutsy they included XaraLX in the ready-built Synaptic packages. That version doesn't allow custom brushes which is a BIG feature for me. As an example, you can draw a group of little hairs and flow the hairs as a group for a line style, thus make a teddy bear with a hair texture. That, and the Synaptic version is 32-bit. For no reason, I like to keep things 64-bit.

I can build the Source code for XaraLX vers. xaralx_0.7r1785-1_amd64.deb (after downloading a lot of libs). Where I go wrong when I build software is: I end up with the software in my Home Folder. To change that, I need to set up an option for the ./configure --preface ...

Where does the binary belong in Ubuntu when you build Software?

Help me on this, and the final thing will be for the SVG import/output module to be added. And, then... I can make a clean .deb for AMD-64bit.

Thanks.

---

### Post by Unterseeboot_234 on 2007-11-13
Okay, I can build but I never know where to put the pieces whenever I

```
./configure --prefix=/usr/share/
```

didn't do anything. I ended up with the binary inside the .configure folder itself. I uninstall my .deb, go back to the Repository version of Xara because they built in the .SVG support. Then, I

```
username@usernamed-desktop:~$ sudo cp '/home/username/XaraLX-0.7r1785/**XaraLX**' '/usr/bin/**xaralx**' 
```

In other words, I replace the Repository binary with my built binary. NOW I have brushes, once again, in XaraLX. I'm happy with everything except I don't have unicode support in XaraLX. If I need an Umlaut " ü ", baby, I draw it.

So, now my question is: can somebody give me a link about using ./configure and its options, so I can build Linux software???

---

### Post by KIAaze on 2007-11-13
The reference for using the autotools (./configure, make, make install) is the autobook:
[http://sourceware.org/autobook/]("http://sourceware.org/autobook/")

Here are the parts that might interest you:
[http://sourceware.org/autobook/autobook/autobook_85.html#SEC85]("http://sourceware.org/autobook/autobook/autobook_85.html#SEC85")
[http://sourceware.org/autobook/autobook/autobook_107.html]("http://sourceware.org/autobook/autobook/autobook_107.html")

As for building a debian package:
[http://www.debian-administration.org/articles/337]("http://www.debian-administration.org/articles/337")
or
[http://linuxdevices.com/articles/AT8047723203.html]("http://linuxdevices.com/articles/AT8047723203.html")

```
./configure --prefix=/usr/share/
make
make install

```
should install the program into /usr/share/ as far as I know.
Did you go all the way to make install?
Because "make" only compiles in the folder where you run it (i.e: where the configure file is).

Also, why did you choose /usr/share/? Do you have write access to it?
I think it makes more sense to use a specially created directory in your home directory.

---

### Post by Unterseeboot_234 on 2007-11-14
Many thanks, KIAaze. Your links were just what I was looking for. Other reference from my research dealt too much with C programming in Linux. I respond to this thread for anyone else following along. My interest in building software comes from my introduction to *buntu, I got in at the Dapper level. Dapper is great -- it's lean and fast -- but Dapper was lacking in 64-bit pre-built software. I had to learn the hard way when building if I tried to substitute a core library that Dapper was using, I broke everything and lost all my data. Gusty is superb. Lots of pre-built software, even 64-bit. I was glad to see XaraLX included, albeit it is a "broken" version.

My trick of building Xara and then copying my build's binary to the Repository version's location on my hard disc did fix the ability to make a brush in my drawings. However, the software no longer allows us to set Options on the custom Brush. Used to be, I could randomize and adjust spacing of the Brush. I'll take what I can get. XaraLX needs refinement and further development that I hope the community will provide. Inkscape is definitely more mature, but goes haywire when building up a drawing with more than 22 elements. XaraLX allows a vast complexity. Xara makes vector art look like bitmap. With Xara, I have to be happy with .png export. The Xara SVG export capability doesn't collaborate with any other software.

I like your suggestion, KIAaze, of just installing my built software(s) to my Home Folder. For no reason, I was thinking software belonged in specific locations within the File System to protect Linux and gain Desktop features like being listed in the Desktop Menus with a pretty Icon. The Menu Icons show how much finesse the Ubuntu development team has to show!

My --prefix-/usr/share did not work, because after I did "make" I did "checkinstall" to gain a .deb -- something very worthwhile. Dapper made a .deb for me in makeHuman. Gutsy won't build makeHuman (64-bit) and thus I regained makeHuman with my old .deb from backups.

---

### Post by KIAaze on 2007-11-14
> **Unterseeboot_234 said:**
> 
I like your suggestion, KIAaze, of just installing my built software(s) to my Home Folder. For no reason, I was thinking software belonged in specific locations within the File System to protect Linux and gain Desktop features like being listed in the Desktop Menus with a pretty Icon. The Menu Icons show how much finesse the Ubuntu development team has to show!


Well, it does belong in a specific location within the filesystem.
At least if you want to make an "official" debian package.

Menu launchers (*.desktop files) are for example placed in /usr/share/applications/. If they aren't placed there, I don't think they'll appear in the menu.

Binaries (programs) are placed in locations as /bin, /usr/bin, /usr/local/bin, /usr/games.

I don't know the official guidelines for creating packages yet, but if you want to make official packages, you'll probably have to install the program into a specific location.

The --prefix=dir option is just there so you can install elsewhere. By default, it's "/".
And it only becomes relevant when you do "make install" which is just moving the built files to where they belong. (to use the program you don't necessarily need to run "make install")

The building itself is done during "make".

P.S: And thanks for telling me about XaraLX. Looks good. :)

---

