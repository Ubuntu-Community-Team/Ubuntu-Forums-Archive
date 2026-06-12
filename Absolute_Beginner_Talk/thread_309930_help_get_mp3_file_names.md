---
title: "help: get mp3 file names"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2006-11-30
Is there an easy way to get file names for mp3 files? I have many mp3 files that I save from tmp folders that have numeric names - but I want to use some sort of script or command or GUI tool to get the actual names of these files. Any help out there? I've tried a few GUI apps but have had no luck. It seems as if there are many GUI apps that require many add-ons in order to work properly...

---

### Post by deadgobby on 2006-11-30
please do not dual post 
see thread
[http://ubuntuforums.org/showthread.php?t=309913](http://ubuntuforums.org/showthread.php?t=309913)

---

### Post by randytuggle on 2006-11-30
With all due respect,this is not a dual post. Now that I have the extensions problem fixed - I would like to know how to retrieve the NAMES for the individual mp3 files. They are numerically tagged and I would like to get the artist+song titles for the files...

---

### Post by Ben Sprinkle on 2006-11-30
You mean the ID3 tag?
Read [this for editing ID3 tags also](http://tldp.org/HOWTO/MP3-HOWTO-13.html).

---

### Post by deadgobby on 2006-11-30
No dis taken. Hope you get the Mp3's playing in no time. Just keep the same thread going. There is oodles of people that are going to help you. It just saves time.
Gobby

---

### Post by CatKiller on 2006-11-30
If the files are properly tagged, then there are tools in Synaptic that will rename them based on the tags. Audio Tag Tool is one, although I can't remember the name of the package.

EDIT: [tagtool]("http://packages.ubuntu.com/dapper/sound/tagtool"), apparently.

---

### Post by randytuggle on 2006-11-30
Yes. ID3 tag info is what I wish to apply to each file. I looked at the link you posted BUT is there an easier way to get this ID3 tag info for multiple files at once? That looks like a lot of individual command work to get names for EACH files I have. I'm a noob, so bear with my stupidity,please.

---

### Post by randytuggle on 2006-11-30
I've tried a few (I think all actually) of the apps in Synaptic - but I can't get any of them to display track names even CLOSE to what the file actually is titled...aargh!

---

### Post by Ben Sprinkle on 2006-11-30
Command line is easier to me.

---

### Post by deadgobby on 2006-11-30
> **Goat Spirit said:**
> Command line is easier to me.

Ditto

Gobby

---

### Post by rajan on 2006-12-06
tagtool worked great for me, but i'm sorta curious how to edit the tag by hand (i.e. using a text editor). open an mp3 and at the top there should be the ide3 tag info, but i'm not sure what the format is, and therefore i can't make changes. anyone know formatting for mp3s? internet searches only give me applications that will do this for me. i know, i know, tagtool is the only thing i need, but i like to know that i could do it by hand if i needed to (being able to figure out how this stuff works is why i switched to linux).

---

### Post by scc4fun on 2006-12-06
> **rajan said:**
> tagtool worked great for me, but i'm sorta curious how to edit the tag by hand (i.e. using a text editor). open an mp3 and at the top there should be the ide3 tag info, but i'm not sure what the format is, and therefore i can't make changes. anyone know formatting for mp3s? internet searches only give me applications that will do this for me. i know, i know, tagtool is the only thing i need, but i like to know that i could do it by hand if i needed to (being able to figure out how this stuff works is why i switched to linux).
See this for starters:
[http://en.wikipedia.org/wiki/ID3#Editing_ID3_tags](http://en.wikipedia.org/wiki/ID3#Editing_ID3_tags)

---

### Post by rajan on 2006-12-07
i understand the concept of a tag, and that there are programs that you can use to edit them. i even get that some tags are different from others. what i can't find (at the wikipedia site either) is what the format of the tag is. that's what i'm asking. does anyone know the formatting of the text part of a tag?

```
ID3^C^@^@^@^@^AvPRIV^@^@^@^N^@^@PeakValue^@]m^@^@PRIV^@^@^@^Q^@^@AverageLevel^@^B^O^@^@TIT2^@^@^@^O^@^@^@Under PressureTPE1^@^@^@^T^@^@^@David Bowie & Queen^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^....lots more @^'s
```

---

### Post by Ben Sprinkle on 2006-12-07
The formatting is called ID3. I think there are other formats also.

---

### Post by rajan on 2006-12-07
i guess i'm just not being clear about what i'm asking....

i'm trying to figure out if there's a way to create a full tag by hand. in order to do that, you have to know how many null spaces are needed between each component of the tag (above), which order the items go in, etc. in my past life as a FORTRAN programmer if i was going to read a certain file i would specify a format such as (f12.3,i4,a4) or something, which corresponds to a real number with 12 overall places and 3 after the decimal, an integer with 4 places, and a character with 4 places. as long as the file was in this format, i would get the real, integer and character out reliably. the "format" i'm looking for is the actual sequence of null spaces, text, and whatever else is in there. 

sorry 'bout the obfuscation

---

### Post by scc4fun on 2006-12-07
> **rajan said:**
> i guess i'm just not being clear about what i'm asking....

i'm trying to figure out if there's a way to create a full tag by hand. in order to do that, you have to know how many null spaces are needed between each component of the tag (above), which order the items go in, etc. in my past life as a FORTRAN programmer if i was going to read a certain file i would specify a format such as (f12.3,i4,a4) or something, which corresponds to a real number with 12 overall places and 3 after the decimal, an integer with 4 places, and a character with 4 places. as long as the file was in this format, i would get the real, integer and character out reliably. the "format" i'm looking for is the actual sequence of null spaces, text, and whatever else is in there. 

sorry 'bout the obfuscation
ID3(v1?) [http://www.mpx.cz/mp3manager/tags.htm](http://www.mpx.cz/mp3manager/tags.htm)

From that article I saw that there are multiple (incompatible) versions of ID3v2, namely 2.3.0 and 2.4.0 as of the date of publication (December 30, **102**).

That's the best I could find on a quick google search.

Ahh, here's the "informal" standard for ID3v2.4.0 from google's cache as id3.org seems to be down today.
[http://www.google.com/search?q=cache:FNGJYvrdgAQJ:www.id3.org/id3v2.4.0-structure.txt+id3v2+tags+format&hl=en&gl=us&ct=clnk&cd=6&client=firefox-a](http://www.google.com/search?q=cache:FNGJYvrdgAQJ:www.id3.org/id3v2.4.0-structure.txt+id3v2+tags+format&hl=en&gl=us&ct=clnk&cd=6&client=firefox-a)

---

### Post by rajan on 2006-12-07
awesome, thanks scc4fun. according to the middle of this section from google's cache, it appears there is no fixed format. 

> ID3v2 is designed to be as flexible and expandable as possible to
   meet new meta information needs that might arise. To achieve that
   ID3v2 is constructed as a container for several information blocks,
   called frames, whose format need not be known to the software that
   encounters them. At the start of every frame is an unique and
   predefined identifier, a size descriptor that allows software to skip
   unknown frames and a flags field. The flags describes encoding
   details and if the frame should remain in the tag, should it be
   unknown to the software, if the file is altered.

thanks again guys

---

