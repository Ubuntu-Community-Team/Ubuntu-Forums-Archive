---
title: "Audio Pattern Recognition"
date: 2008-03-23
forum: Assistive Technology &amp; Accessibility
---

### Post by naurus on 2008-03-23
Hello.  I'm looking for speech recognition software. In a sense.  All the software needs to be able to do is recognize patterns in streaming audio, not actually follow a conversation.  Am example would be for me to say (this is very star treky) "Computer!" and the software would recognize that I've said this because it's been  trained to listen for audio with a pattern sort of like it.  The computer would respond with "Yes?" and await another PRESET command like "Play some music" which would open up Amarok and start it playing.  This couldn't be too hard since even 3 year old cell phones can do it.  Well, cellphones don't stream the audio, but if the software were to capture one second of audio, then compare it, it may work just fine.

Is this possible?  Even better: Is this possible for free?

Any help is greatly appreciated. Thanks!
Naurus

---

### Post by Jiffyman on 2008-03-24
I found an article here: [http://www.linux.com/feature/113917](http://www.linux.com/feature/113917)

I hope this is sorta what your looking for. By the way thanks for a splendid Idea. I've tried software like this for windows and it sucked, but this may be better designed than some. Like I said never tried it, but I'm going too. I'll let you know how it goes. .

---

### Post by designwiz on 2008-04-07
Theres an application that works flawlessly for me that suits ur description

Perlbox Voice is an voice enabled application to bring your desktop under your command. With a single word, you can start your web browser, your favorite editor or whatever you want. 

What you need first:

1.)Perl-Tk, the graphical toolkit for perl. This should come with your distribution, if not ```
sudo apt-get install perl-tk
```

2.)Sphinx2, the speech to text engine for Perlbox Voice. 

Get the Sphinx2-bin
```
sudo apt-get install sphinx2-bin
```


3.)Festival, the text to speech engine for Perlbox Voice. 
```
sudo apt-get install festival 
```

After you are done with this, you can now proceed to install perlbox

```
sudo apt-get install perlbox-voice
```

or you could also click here to download[http://downloads.sourceforge.net/perlbox/perlbox-voice-0.09.noarch.deb?modtime=1125791444&big_mirror=0]("http://downloads.sourceforge.net/perlbox/perlbox-voice-0.09.noarch.deb?modtime=1125791444&big_mirror=0")

Hope this helps if you have any problems do feel free to ask!
Cheers:guitar:

---

