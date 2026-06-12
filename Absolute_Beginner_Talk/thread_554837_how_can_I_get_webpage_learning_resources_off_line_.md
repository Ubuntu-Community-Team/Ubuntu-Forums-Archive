---
title: "how can I get webpage learning resources off line and printable"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by iansane on 2007-09-19
Hi everyone, 

I have difficulty spending hours in front of my computer screen reading about Ubuntu and OS's in general but I have found several on line resources that I am actually understanding and learning from. I have tried downloading pages and  websites with wget and that works for offline reading but I want to convert those pages to PDF so I can print them off and read as a book. Is there an easier way to get all of the pages with pictures intact, all into one printable form? Also, how reliable are wikipedia pages when it comes to learning about kernels, abstraction layers, API's, ETC. ? Many of the online resources seem easier to understand than most books I've tried to learn from. Thanks

---

### Post by cubeist on 2007-09-19
If you are using firefox you can can choose "save page as" and select the option of "complete web page"... then you can open it offline anytime...

---

### Post by iansane on 2007-09-19
right, but then I want to print it with pictures intact so I can read it without my computer and I wanted to see if there is an easy way to save all the pages in an article without haveing to go to each link individually and save each page, and I want to get rid of the extra folder of files that comes with it when you save as complete web page. Is this possible?

---

### Post by iansane on 2007-09-19
Basically I want a PDF of the page without anything missing. Exept for the ads and banners. I wish they would go away but I guess that's the price you pay for free services and resources. I can work around it with copy and paste but I wish every page had a link to a printable version. Thanks

---

### Post by Maestro23 on 2007-09-19
> **iansane said:**
> Basically I want a PDF of the page without anything missing. Exept for the ads and banners. I wish they would go away but I guess that's the price you pay for free services and resources. I can work around it with copy and paste but I wish every page had a link to a printable version. Thanks

Have you tried:

File>> Print>> Print to file

Should be able to open the saved in your .pdf reader.

---

### Post by iansane on 2007-09-19
> **Maestro23 said:**
> Have you tried:

File>> Print>> Print to file

Should be able to open the saved in your .pdf reader.

thanks, I guess I could do that to print to a tiff in windows. I never tried it. This way in ubuntu  saves it as a .ps file.  Is that like a tiff? How can I convert it to a pdf so it can be read or printed on any platform?
I tried uploading to LOOP for firefox and it isn't working.
Also how do I open with adobe if it's not a pdf? I right clicked and chose "open with another program" and adobe reader isn't there. It is installed though. Tried custom command and there is a command called acroread. Is that like the reader.exe in windows? Sorry I don't remember the exact name but I know it when I see it if I browse for a program to open with. This is just confusing to me cause I'm used to everything having an exe

---

### Post by iansane on 2007-09-21
Just in case anyone else wants to be able to unplug for a while and still have their online resources, here's how I solved my problem.

I used the file>print> and print to file

then put all the ps files in my share folder located on my windows drive. (only works if you still have windows)

then installed ghostscript and gsview on windows

used gsview to convert  the ps to pdf

Had to add the .pdf to the name when saveing or it just calls it "file" It will open with adobePDF through "open with"  but will not be associated if you don't add the extension.

Now I have a cross platform, exact copy of webpages that I can print off or view on any computer.

I know there is a ghostscript version for linux but I could not figure out how to install it. Can some one with nothing better to do, post a step by step on installing ghostscript (or a better converter if you know of one) to ubuntu through terminal? If not it's cool, problem solved with a simple .exe I would like to learn the Ubuntu way though, so I'm reading up on all the links I've been getting here. One day I can do away with that cursed M$ Window$.

---

### Post by Irihapeti on 2007-09-21
ghostscript is in the repositories as gs-common, gs-esp, gs-epl. 

```
sudo apt-get install gs-common
```
will get you the first two, I think, or use synaptic if you prefer. I'm a bit vague on this as I installed ghostscript as a dependency of another program; I usually don't keep notes and I tend to forget the details after several weeks:-)

I've got these installed and I can read files printed as PS from firefox with Evince (the Gnome default PDF viewer) no problem.

Another option, for windows, is to install doPDF as a printer. It generates .pdf files from any program. It has the occasional rendering problem but nothing that affects readability. Again, I can't remember where I got it but I guess google would know.

HTH
Irihapeti

---

### Post by HereInOz on 2007-09-21
Or you can use the command line utility 

ps2pdf

in the format of:

ps2pdf input_filename output_filename

---

### Post by Maestro23 on 2007-09-21
> **HereInOz said:**
> Or you can use the command line utility 

ps2pdf

in the format of:

ps2pdf input_filename output_filename

Now that is a handy little command.  Thanks for the heads-up. :smile:

---

### Post by iansane on 2007-09-21
> **HereInOz said:**
> Or you can use the command line utility 

ps2pdf

in the format of:

ps2pdf input_filename output_filename

I tried that with a file called mountCommands and heres what I got. This error and a pdf of a blank page that opens with adobe just fine but is blank. I tried with and without the .ps at the end and got smae thing both times. Any suggestions?

ian@lotustest:~$ cd Desktop
ian@lotustest:~/Desktop$ ps2pdf input_mountCommands.ps output_testcommands
ERROR: /undefinedfilename in (input_mountCommands.ps)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1124/1686(ro)(G)--   --dict:0/20(G)--   --dict:102/200(L)--
Current allocation mode is local
Last OS error: 2
ESP Ghostscript 815.04: Unrecoverable error, exit code 1
ian@lotustest:~/Desktop$ 

also is gs a terminal based tool? I don't have anything on the apps menu after installing it.

---

### Post by Irihapeti on 2007-09-21
What I did was to print the page from Firefox, selecting Postscript/default as printer name, and checking the Print to File box. Then I double-clicked on the resulting file icon and it opened. Actually, even before I opened it, the icon showed a preview of the document.

Irihapeti

---

### Post by Maestro23 on 2007-09-21
> **iansane said:**
> I tried that with a file called mountCommands and heres what I got. This error and a pdf of a blank page that opens with adobe just fine but is blank. I tried with and without the .ps at the end and got smae thing both times. Any suggestions?

ian@lotustest:~$ cd Desktop
ian@lotustest:~/Desktop$ ps2pdf input_mountCommands.ps output_testcommands
ERROR: /undefinedfilename in (input_mountCommands.ps)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1124/1686(ro)(G)--   --dict:0/20(G)--   --dict:102/200(L)--
Current allocation mode is local
Last OS error: 2
ESP Ghostscript 815.04: Unrecoverable error, exit code 1
ian@lotustest:~/Desktop$ 

also is gs a terminal based tool? I don't have anything on the apps menu after installing it.

Try just:

> ps2pdf input_mountCommands output_testcommands

---

### Post by iansane on 2007-09-22
> **Irihapeti said:**
> What I did was to print the page from Firefox, selecting Postscript/default as printer name, and checking the Print to File box. Then I double-clicked on the resulting file icon and it opened. Actually, even before I opened it, the icon showed a preview of the document.

Irihapeti

mine does that too, No prob. It just doesn't open in adobe cause it's not a pdf, It opens with Ubuntu's document viewer,  and in windows adobe says .ps is an unsupported file format so to make it cross platform, it needs to be able to be converted to a pdf. Like I said, I now have ghost script in windows to do my converting for me. Thanks

---

### Post by iansane on 2007-09-22
> **Maestro23 said:**
> Try just:

Yep, same error message. It's very possible that I don't have something installed or configured right. I'll work on it. Thanks

---

### Post by Irihapeti on 2007-09-26
iansane:

I've discovered cups-pdf in the repositories. It allows one to generate pdf files directly from Firefox. It works with the postscript drivers from several printers. I've tested it with generic/colour laser and one of the HP colour laserjet drivers.

---

