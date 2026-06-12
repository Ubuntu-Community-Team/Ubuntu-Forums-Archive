---
title: "Where did it go?!"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Minyaliel on 2005-10-30
I installed LilyPond (music notation software) some time ago, but it doesn't show up on the applications menu! Where did it go?

---

### Post by Mustard on 2005-10-30
To run something that doesnt have a menu entry you need to open it using a terminal by typing the name of the application and hitting the enter key.  If you are not sure what a program is called type the first few letters in then hit tab twice to bring up a list of apps that start with those letters.  The terminal in Breezy can be found in Applications>>Accesories menu.

Once you know what the name of the application is and how to run it from terminal, you can go to Applications>>System>>Application Menu Editor and add a new entry for the application in question.

---

### Post by Minyaliel on 2005-11-04
Alright, thanks, I'll try that. :)

---

### Post by Minyaliel on 2005-11-04
Well, I got a long list of something... since I'm using a translated version of ubuntu, there's probably no use in reposting it... but I didn't really get any further :P

---

### Post by Lambert on 2005-11-04
there are different way to do this but you could hit alt+f2. This brings up a run dialog. start typing lily and if there's nothinig else similar as an executable it will fill in the blank and run the program.

What you're looking for is probably in /usr/bin or /usr/local/bin

If you don't know the exact program verbage, you can type in a terminal

```
apropos lily or apropos pond
```

This will give you a list of items that somewhat match lily. You should see your program. 

From here type

```
whereis <program_name>
```


It will then show you where it's at. Then do like previous post said. You can edit the applications menu adding this to it.

---

### Post by Minyaliel on 2005-11-04
I can't get it to run, though... Look, this is what I'm getting. 

minyaliel@minyaliel:~$ apropos lily
LilyPond (1) [lilypond-bin] - manual page for LilyPond 2.2.6
lilypond (1)         - manual page for lilypond 2.2.6
lilypond-bin (1)     - manual page for LilyPond 2.2.6
lilypond-book (1)    - manual page for lilypond-book 2.2.6
minyaliel@minyaliel:~$ whereis lilypond
lilypond: /usr/bin/lilypond /usr/lib/lilypond /usr/bin/X11/lilypond /usr/share/l ilypond /usr/share/man/man1/lilypond.1.gz
minyaliel@minyaliel:~$ lilypond
Brug: lilypond [FLAG]... FIL

Run LilyPond, add titles, generate printable document.

Flag:
  -d, --dependencies             skriv Makefile-afh\uffffngigheder for hver inddatafi l
  -h, --help                     denne hj\ufffflp
      --debug                    skriv \uffffnnu mer utdata
  -f, --find-pfa=FIL             find pfa-skrifttyper brugt i FIL
      --html                     skapa en HTML-fil som l\uffffnkar till all utdata
  -I, --include=KATALOG          tilf\uffffj KATALOG til LilyPonds s\uffffgesti
  -k, --keep                     behold al uddata, udskrivo i kataloget lilypond .dir
      --no-lily                  k\uffffr ikke LilyPond
  -m, --no-paper                 lav kun MIDI-uddata
  -o, --output=FIL               skriv uddata til FIL
      --preview-resolution=RES   s\ufffftt resolutionen f\uffffr f\uffffrhandsgranskningen till  RES
      --no-pdf                   do not generate PDF output
      --no-ps                    do not generate PostScript output
  -p, --pdf                      lav PDF-uddata
  -P, --postscript               lav PostScript-uddata
      --pdftex                   use pdflatex to generate PDF output
      --png                      skapa PNG-sidbilder
      --preview                  skapa en bild av det f\uffffrsta systemet
      --psgz                     skapa PS.GZ
  -s, --safe-mode                run in safe-mode
  -S, --set=N\uffffGLE=V\uffffRDI          \uffffndr global indstilling N\uffffGLE til V\uffffRDI
  -V, --verbose                  v\uffffr udf\uffffrlig
  -v, --version                  vis versionsnummer
  -w, --warranty                 vis garanti og copyright


Rapport\uffffr programfejl til [email]bug-lilypond@gnu.org[/email]
.Rapport\uffffr fejl i overs\uffffttelsen til <dansk@klid.dk>.
lilypond: error: ingen filer angivne p\uffff kommandolinjen.
minyaliel@minyaliel:~$ lilypond.1.gz
bash: lilypond.1.gz: command not found
minyaliel@minyaliel:~$

What's wrong?

---

### Post by Mustard on 2005-11-05
The first time you just typed 'lillypond' it was close, but you have no options set, so it listed the options you could run it with.  Try typing either 

```
man lilypad #opens manual for lilypond

or if that doesnt work try

info lilypond
```
 
This should load a manual for lilypond in terminal.

I did notice you attempted to open the manual when you tried lilypond.1.gz, but what you may not have realised is that, firstly you need to be in the correct directory that lilypond.1.gz is in, and it is compressed file (like a zip file from windows).  You can open compressed files using gunzip command, but you would need to find the directory it is stored in.  You can do that easily enough by going to your Places menu and using the Search for Files function and doing a search on your Filesystem.

I know this all sounds quite complex but it doesnt take long till it all becomes second nature.

Some further reading for you would be the manual for gunzip, using the command, man gunzip.

If you would like a more rapid help with the issue, you could try joining the Ubuntu IRC help channel, using your x-chat client in your Applications>>Internet menu.  It's already set up with the Ubuntu servers listed in the Server LIst and it will automatically join #ubuntu, the official help channel for ubuntu.

For manual configuration of an IRC client;
Server: irc.freenode.net Port:6667
Channel: #ubuntu

---

