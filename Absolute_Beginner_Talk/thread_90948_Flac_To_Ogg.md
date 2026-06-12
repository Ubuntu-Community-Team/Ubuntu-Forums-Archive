---
title: "Flac To Ogg?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-11-16
Is there a utility that can convert FLAC to OGG (music format)?

thanks!

---

### Post by Wolki on 2005-11-16
[QUOTE=garnertr]Is there a utility that can convert FLAC to OGG (music format)?
[/QUOTE]

Sound Converter, it's in the repos. You could also use the command line ogg encoder "oggenc".

---

### Post by apjone on 2005-11-16
[QUOTE=garnertr]Is there a utility that can convert FLAC to OGG (music format)?

thanks![/QUOTE]

do a 
$sudo apt-get install flac

then at the command line 

flac -d --ogg filename

---

### Post by jacek2v on 2005-11-29
[QUOTE=apjone]do a 
$sudo apt-get install flac

then at the command line 

flac -d --ogg filename[/QUOTE]

From man :
*"--ogg  When  encoding,  generate Ogg FLAC output instead of native FLAC.  Ogg FLAC streams are FLAC streams wrapped in an Ogg transport layer.  The resulting file should have an &#8217;.ogg&#8217; extension and will still be decodable by flac."*

You change wrapping format only.

Oggenc isn't working now (no flac support in Breezy64bit) - in Hoary was working :(

PS. Sorry, my english is very weak.

---

### Post by jacek2v on 2005-12-27
[QUOTE=jacek2v]From man :
*"--ogg  When  encoding,  generate Ogg FLAC output instead of native FLAC.  Ogg FLAC streams are FLAC streams wrapped in an Ogg transport layer.  The resulting file should have an &#8217;.ogg&#8217; extension and will still be decodable by flac."*

You change wrapping format only.

Oggenc isn't working now (no flac support in Breezy64bit) - in Hoary was working :(

PS. Sorry, my english is very weak.[/QUOTE]
[B]
Self update :[/B]
Oggenc working good !!!! I make a mistake and set MP3 TAGing in CDRIP, then oggenc and others application don't recognize *.flac files.

---

