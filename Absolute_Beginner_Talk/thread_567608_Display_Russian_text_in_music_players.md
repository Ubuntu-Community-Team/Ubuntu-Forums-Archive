---
title: "Display Russian text in music players?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2007-10-04
I've having trouble displaying Russian text in music players in Ubuntu 7.04 (and all the previous ones too).

Everything is displayed in some kind of odd characters. Russian text everywhere else works just fine though. I've read up on it, and apparently it's a problem with the way the MP3 tags are encoded.

Does anyone know how to fix the problem? From what I've heard it doesn't exist in KDE and only effects programs in Gnome, but I can't switch at this time.

I've attached a screenshot of Amarok with the problem.

Edit: I've googled this problem (that's how I know it doesn't effect KDE) but haven't been able to find a solution.

---

### Post by michael37 on 2007-10-05
Same problem here, but for me some mp3 files have readable fonts (correct encoding?) and some have "funny" characters.

I put those tags myself on Windows using foobar2000, so I wonder why the encodings are different.

P.S.  What is the best utility to edit mp3 tags?

---

### Post by michael37 on 2007-10-05
Another tidbit.  Easytag cannot read any of my tags, even after I changed the default encoding to UTF-8 in preferences.

---

### Post by tgalati4 on 2007-10-05
You need ID3V2.4 tags with UTF-8.  Unfortunately, most players only read ID3V2.2 or 2.3 with and without UTF-8 encoding.  

UTF-8 is needed for international character sets and I believe the latest version of easytag can write 2.4 tags, however I was not able to compile it on Dapper.  Too many unmet dependencies.

I have an iPod that I use with iTunes on a Mac and I want consistent tags between the Mac and music players in Ubuntu.  This is a challenge.  I still haven't got it figured out completely yet.

---

### Post by michael37 on 2007-10-05
I found something after a little bit of research... hope it helps.

1. Install Quod Libet (sudo apt-get install quodlibet-plugins quodlibet)
2. Start Quod Libert and select  Music -> Plugins
3. Enable "Convert Encoding" plugin
4. Import your music (maybe just a few files for the test).
5. Right click on any file which looks like funny characters and select Edit Tags
6. In Edit Tags tab, right click on any tag, select "Convert Encoding" and choose something that reads like Russian.

It works for me, but I can't imagine clicking on EVERY tag of EVERY mp3 and correcting it.  Hope there is a better automated way.

---

### Post by michael37 on 2007-10-05
> **tgalati4 said:**
> You need ID3V2.4 tags with UTF-8.  Unfortunately, most players only read ID3V2.2 or 2.3 with and without UTF-8 encoding.  

UTF-8 is needed for international character sets and I believe the latest version of easytag can write 2.4 tags, however I was not able to compile it on Dapper.  Too many unmet dependencies.

I have an iPod that I use with iTunes on a Mac and I want consistent tags between the Mac and music players in Ubuntu.  This is a challenge.  I still haven't got it figured out completely yet.
I am running Fiesty and it has only EasyTag 2.1.

---

### Post by michael37 on 2007-10-05
Ex Falso comes installed with Quod Libet.  It provides identical editing capabilities with Convert Encoding.

---

### Post by hugmenot on 2007-10-05
Maybe this will help ya. Mutagen is the tagging library behind EF/QL.
It comes with a few command line tools. One of them is midiconv, which can be used in a script.

I know that it will convert files from an encoding to UTF and use the proper 2.4 tags, that support unicode

```
find . -iname *.mp3 -exec [COLOR="SeaGreen"]mid3iconv --remove-v1 -e ENCODING -pd[/COLOR] "{}" \;
```

In green is the actual command, you have to find out what to place as ENCODING there. The outer stuff recurses through all your directories, so start the command in the top folder with the affected mp3s. If the command outputs the correct cyrillic, you can remove -pd and run again, this time changes will be written.

```
Usage: mid3iconv [OPTION] [FILE]...

Mutagen-based replacement the id3iconv utility, which converts ID3 tags from
legacy encodings to Unicode and stores them using the ID3v2 format.

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -e ENCODING, --encoding=ENCODING
                        Specify original tag encoding (default is UTF-8)
  -p, --dry-run         Do not actually modify files
  --force-v1            Use an ID3v1 tag even if an ID3v2 tag is present
  --remove-v1           Remove v1 tag after processing the files
  -q, --quiet           Only output errors
  -d, --debug           Output updated tags

Files are updated in-place, so use --dry-run first.
```

---

### Post by tgalati4 on 2007-10-05
Easytag 2.1 is the latest stable version (or nearly so).  In the preferences (under "Tag" or "ID3" there are selections for different ways to convert to UTF.  You can convert entire directories at once, but be careful, because it can also screw up entire directories of files.  Try some tests first.  You may have better luck with Feisty getting the latest development version Easytag.  This is one area that is undergoing rapid change.

Some mp3 players will choke on 2.4 tagging--mainly older players but surprising some newer players get tripped up as well.

Let us know what ultimately works for you.

---

### Post by michael37 on 2007-10-06
> **tgalati4 said:**
> Easytag 2.1 is the latest stable version (or nearly so).  In the preferences (under "Tag" or "ID3" there are selections for different ways to convert to UTF.  You can convert entire directories at once, but be careful, because it can also screw up entire directories of files.  Try some tests first.  You may have better luck with Feisty getting the latest development version Easytag.  This is one area that is undergoing rapid change.

Some mp3 players will choke on 2.4 tagging--mainly older players but surprising some newer players get tripped up as well.

Let us know what ultimately works for you.

See my [my post above in this thread](http://ubuntuforums.org/showpost.php?p=3478025&postcount=3).  Easytag 2.1 in Fiesty cannot handle any Russian mp3 tags, even those that VLC and QuodLibet can handle.

Maybe bug in their UTF implementation.

---

