---
title: "Archive Converter"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-08
[COLOR=DarkRed]**I'd like to inform everyone right off the bat that this is only a beta version of 0.0.1!!**[/COLOR]

That being said, I will explain this a little more. "Archive Converter" is a tool I'm building to give users the ability to easily pick and archive (.tar.gz and the like), choose a new format, and have it automatically converted for them!  At the moment, I can see it being hard to use for the average user and in addition to that there is very little flexibility and it also currently only supports converting between .tar, .tar.gz, and .tar.bz2.  In the future I hope to make it significantly more easy to use, add a ton of features, and of course expand it's range of able formats, but at th moment I just wanted to give all you a look at what I'm doing with all my spare time ;)

It also does not have a license at the moment, but I would have to discourage anyone from trying to put work into this except for personal experimentation, and **redistribution ist verboten!!** er, strictly prohibited :rolleyes:

PS: You will notice there is indeed a "rm -r -f" in the code... I would say if you know why this is not a danger (by reading the script) then you are an advanced enough user to use this script ;)

[COLOR=DarkRed]Why? It's certainly not fool proof, it may not work on locations with spaces (but inside the archive is OK) and like I said its still 0.0.1 and in testing!![/COLOR]  Although it seems stable as far as the tests I've done...

[:KS LOOK HERE :KS]("http://www.mediafire.com/?9yc1unzdisp") It's a little screen recording showing a successful conversion of an archive from .tar.bz2 to .tar.gz

---

### Post by blueridgedog on 2008-01-09
You could simplify the process by piping one untaring/unzipping process to another taring/zipping process with a single command, without the need to deal with the temporary location/files.

---

### Post by asmoore82 on 2008-01-09
> **ryanVickers said:**
> [COLOR=DarkRed]**I'd like to inform everyone right off the bat that this is only a beta version of 0.0.1!!**[/COLOR]
...
It also does not have a license at the moment, but I would have to discourage anyone from trying to put work into this except for personal experimentation, and **redistribution ist verboten!!** er, strictly prohibited :rolleyes:
...


[SIZE="2"]Is this some kind of a sick Joke?[/SIZE]

Adam sM

P.S. it is a *_**complete**_* *_waste_* of time to actually extract
and recreate a tarball just to change the compression method

---

### Post by ryanVickers on 2008-01-09
> **blueridgedog said:**
> You could simplify the process by piping one untaring/unzipping process to another taring/zipping process with a single command, without the need to deal with the temporary location/files.

Ok, good idea I'll try it

---

### Post by ryanVickers on 2008-01-09
> **asmoore82 said:**
> [SIZE=2]Is this some kind of a sick Joke?[/SIZE]

Adam sM

P.S. it is a *_**complete**_* *_waste_* of time to actually extract
and recreate a tarball just to change the compression method

um... no I just like to make things... and I think it's not worth anyones time to help change the code though... just give me a quick idea if you got one and let me do it... :p

---

### Post by blueridgedog on 2008-01-09
> **asmoore82 said:**
> [SIZE="2"]Is this some kind of a sick Joke?[/SIZE]

Adam sM

P.S. it is a *_**complete**_* *_waste_* of time to actually extract
and recreate a tarball just to change the compression method

Though I agree, I assumed the OP was doing it as an exercise in coding.

---

### Post by ryanVickers on 2008-01-09
And if you had a bunch of strange odd ball formats you wanted to standardize, you should use this! (although granted, at the time the formats  it supports are not the ones you would want to convert from... just to...)

---

### Post by blueridgedog on 2008-01-09
Oh, I think it has merit and it also shows integration between the shell and the window environment.  Personally, all the tarballs I create use the same format and all those I download are used then destroyed.

---

