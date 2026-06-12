---
title: "Linux script to replace line breaks in a file?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by gstuart on 2007-05-11
Hello:  I want to find and replace line breaks in a file, using a shell (.sh) script.  Using Gedit, I can replace two lines each containing two dashes (-- i.e. - - without the space), 

--
--

with 

--

in an open text file by searching for

--\n--

and replacing it with 

--

However, when I try to specify this using the 'replace' command

replace "target text" "replacement text" -- output_file.txt

in a subsection of my linux script file (making sure that I "escape" i.e. prefixing the dashes with a backslash, i.e. \-), I cannot get it to work.  I tried, unsuccessfully,

replace "\-\-\n\-\-" "TEST_TEST_TEST" -- my_output_path_and_file.txt

and various permutations. including wildcards.

However, 

replace "\-\-" "TEST_TEST_TEST" -- my_output_path_and_file.txt

does work, but only on single lines, and it does not find/replace line breaks!

So, what's the easiest way to find and replace line breaks in a target file, using a shell script?

Thanks, appreciated - Greg   :-)

---

### Post by hyper_ch on 2007-05-11
PHP would be simple... you have php isntalled?

---

### Post by vikram on 2007-05-11
the tr command should do the trick and is already installed.
```

cat fileName | tr -d "\n"

```


look at [http://linux.about.com/library/cmd/blcmdl1_tr.htm](http://linux.about.com/library/cmd/blcmdl1_tr.htm) for more info.

---

### Post by gstuart on 2007-05-12
Thank you for your kind replies.  Based on the last suggestion - the tr command - I  added the following lines to my bash script, that more-or-less accomplishes my goal, as stated at the top of this thread:

# This removes all -- followed by a line break (\n): \n\-\-  ;  Note that \-\-\n does *not* work:
# cat ~/tv/xmltv_scripts/temp.txt | tr  "\n\-\-" "\n" > ~/tv/xmltv_scripts/temp.txt
# This does the same thing:
# cat ~/tv/xmltv_scripts/temp.txt | tr  -d "\-\-" > ~/tv/xmltv_scripts/temp.txt

cat ~/tv/xmltv_scripts/temp.txt | tr  -d "\-\-" > ~/tv/xmltv_scripts/temp.txt
replace "START" " *********  START"	-- ~/tv/xmltv_scripts/temp.txt

Ideally, I would like to separate each program listed with a blank line (i.e. actually *insert* a line break, where needed), but I'm unable to figure out how to do that.  The modified output is adequate, however.  The purpose of all of this is that the bash script that I wrote takes my XMLTV (television) listings from labs.zap2it.com, searches it for specified keywords, dumps the surrounding lines of text to a file, and lastly converts the channel codes and dates/times to a friendly (readable) format.

The changes I implemented, here, modify my output file as indicated in this snip,

From this:

Fri, 11 May 2007 23:42:12 -0400


--
--
--
--
--
START:  May 16, 2007  03:30 pm;  STOP:  May 16, 2007  04:30 pm;  CHANNEL:  36 COM
 MAD TV
 Skateboarder Tony Hawk guest stars; Chingy performs; Queer Eye for the Strange Guy sketch.
--
START:  May 17, 2007  01:00 pm;  STOP:  May 17, 2007  02:00 pm;  CHANNEL:  36 COM
 MAD TV
 Skateboarder Tony Hawk guest stars; Chingy performs; Queer Eye for the Strange Guy sketch.
--
--
--
START:  May 17, 2007  10:00 pm;  STOP:  May 17, 2007  10:30 pm;  CHANNEL:  44 COURT
 Forensic Files
 Nailed
 A woman is killed weeks before testifying against the man who sexually assaulted her.

[ ... etc ...]

To this:

Fri, 11 May 2007 23:44:17 -0400


 *********  START:  May 16, 2007  03:30 pm;  STOP:  May 16, 2007  04:30 pm;  CHANNEL:  36 COM
 MAD TV
 Skateboarder Tony Hawk guest stars; Chingy performs; Queer Eye for the Strange Guy sketch.
 *********  START:  May 17, 2007  01:00 pm;  STOP:  May 17, 2007  02:00 pm;  CHANNEL:  36 COM
 MAD TV
 Skateboarder Tony Hawk guest stars; Chingy performs; Queer Eye for the Strange Guy sketch.
 *********  START:  May 17, 2007  10:00 pm;  STOP:  May 17, 2007  10:30 pm;  CHANNEL:  44 COURT
 Forensic Files
 Nailed
 A woman is killed weeks before testifying against the man who sexually assaulted her.

[ ... etc ...]

Thanks once again for your help - appreciated!  Greg  :-)

---

