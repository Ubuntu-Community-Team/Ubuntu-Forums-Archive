---
title: "Convert WAV to MP3"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2005-10-22
Simple question here.

I have the mp3 codecs installed on my machine.  I am running Ubuntu Hoary.  I have recorded myself singing using the recording application and my microphone.  Now that I have the wav file of myself singing, I want to convert it to mp3 format so I can share the file with my friends.

Using apt-get, what program do I install to convert the file?  I'm familiar with manpages so after it's installed I can use a command line program if thats all that is available.

*Nevermind.  I found lame.

---

### Post by Jenda on 2005-10-22
The ideal user: Asks. Answers.

Imagine if you hadn't posted the above, sooner or later someone would've and someone else would have to answer, probably someone who had to waste their time in someone else's interest. The former can now, instead of posting this question, read the answer straight away, since you, a person who actually did it for his own self, posted it right here...

---

### Post by landotter on 2005-10-22
Grab Audacity via Synaptic, it's a great basic recording program and can export mp3/ogg. I've digitized a lot of vinyls with it and had marvelous success.

[http://audacity.sourceforge.net/]("http://audacity.sourceforge.net/")

---

### Post by Dr. Nick on 2005-10-22
I know you already found a solution but using soundconverter is another solution avaible in synaptic, this seemingly not well known full GUI will convert to and from many formats , including ogg and mp3. It also does batch processing to do alot at once. Just throwing it out incase someone sees this and wants a nice gui to do all the work :)

---

### Post by zerhacke on 2005-10-22
Gui's are nice to have much of the time.  I'm a CLI freak, so I'm happy with lame.

For those trying to use lame, a basic line that will get you an mp3 from a wav would be "lame -h input.wav output.mp3" assuming you're working in the directory the wav file is located.

lame -? for help.

---

### Post by cowlip on 2005-10-22
[QUOTE=Dr. Nick]I know you already found a solution but using soundconverter is another solution avaible in synaptic, this seemingly not well known full GUI will convert to and from many formats , including ogg and mp3. It also does batch processing to do alot at once. Just throwing it out incase someone sees this and wants a nice gui to do all the work :)[/QUOTE]

Thanks!!

---

### Post by Jenda on 2005-10-23
[QUOTE=landotter]Grab Audacity via Synaptic, it's a great basic recording program and can export mp3/ogg. I've digitized a lot of vinyls with it and had marvelous success.

[http://audacity.sourceforge.net/]("http://audacity.sourceforge.net/")[/QUOTE]
Interesting. How did you proceed to do this? Hardware 'n' all. I have a few vinils I'd like to slurp up through a wire...

---

### Post by landotter on 2005-10-23
[quote=Jenda]Interesting. How did you proceed to do this? Hardware 'n' all. I have a few vinils I'd like to slurp up through a wire...[/quote]

Simple, just feed a pre-amped feed of your source into the line-in jack.

I used the "tape-out" output on the back of my old receiver, but modern amps might not have this, so you can just feed the turntable through a seperate pre-amp. I used a mini jack to rca cable to connect--some sound cards can take rca directly. Use the best cable you can find.

---

### Post by Jenda on 2005-10-23
Cool. Thanks.

---

