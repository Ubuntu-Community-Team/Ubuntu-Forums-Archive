---
title: "Burning cds?"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by aum11 on 2005-07-09
I have recently installed Ubuntu 5.04 and I love it!!
However, I have been unable to find clear guidance in the forums on what to do with MANY albums stored in Windows Media Player under Windows xp(wma format)?
 I need to be able to access them in order to burn cds from them.  It would be nice to be able to  play them also under Ubuntu. I hardly ever go back to Windows any more.

Am I best to convert them to ogg or mp3, or will the losses be too great?

What software to use?

Is there s/w to burn direct from wma format(the files of course can be read from ntfs partition)?

I appreciate your help.

---

### Post by petehall on 2005-07-09
The following link details my experiences with converting audio files between different formats. You want to convert the WMAs to WAV files (using mplayer) and then the WAVs to MP3 (using lame). The script that I wrote will do them an album at a time. It's a quite time-consuming process.

[Converting file formats](http://www.uborka.nu/ubi/001291.html)

---

### Post by emmet on 2005-07-09
Hi,

I think there is more than just one question/answer here.

The first question is that yes, you can - in general - play wma files in Linux. If you haven't already, then I recommend the ubuntuguide, specifically this section:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) 

Since you say you are new to Ubuntu, then I recommend you just go through the whole thing to see what's there and what you can install.

Hope this helps!

Emmet

---

### Post by aum11 on 2005-07-09
Thanks for your prompt replies.

Petehall, I have questions about the process You describe of wma to wav and then to mp3.
What will happen to the quality of sound when following this path?
Am I better to try to reload the albums from their cd source?
Is ogg better quality compression than MP3?
What s/w to play and burn?
Ta. O:)

---

### Post by aum11 on 2005-07-10
bump

---

### Post by emmet on 2005-07-11
What does "bump" mean? 

If you're impatient to for an answer, then try googling....for instance:

[Googling for "Ogg"](http://www.google.com/search?q=ogg+&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-GB:unofficial) 

...leads us to the vorbis web site. Where (on the FAQ - link from first page) they state:
> [I]
 Can I convert my MP3 collection to the Ogg Vorbis format?[/I]

    You can convert any audio format to Ogg Vorbis. However, converting from one lossy format, like MP3, to another lossy format, like Vorbis, is generally a bad idea. Both MP3 and Vorbis encoders achieve high compression ratios by throwing away parts of the audio waveform that you probably won't hear. However, the MP3 and Vorbis codecs are very different, so they each will throw away different parts of the audio, although there certainly is some overlap. Converting a MP3 to Vorbis involves decoding the MP3 file back to an uncompressed format, like WAV, and recompressing it using the Ogg Vorbis encoder. The decoded MP3 will be missing the parts of the original audio that the MP3 encoder chose to discard. The Ogg Vorbis encoder will then discard other audio components when it compresses the data. At best, the result will be an Ogg file that sounds the same as your original MP3, but it is most likely that the resulting file will sound worse than your original MP3. In no case will you get a file that sounds better than the original MP3.

    Since many music players can play both MP3 and Ogg files, there is no reason that you should have to switch all of your files to one format or the other. If you like Ogg Vorbis, then we would encourage you to use it when you encode from original, lossless audio sources (like CDs). When encoding from originals, you will find that you can make Ogg files that are smaller or of better quality (or both) than your MP3s.

    (If you must absolutely must convert from MP3 to Ogg, there are several conversion scripts available on Freshmeat.)


As to you second question, the answer is on the [Ubuntu Guide](http://www.ubuntuguide.org) site. A hint in the right direction could be here:

[http://www.ubuntuguide.org/#gnomebaker](http://www.ubuntuguide.org/#gnomebaker) 

Maybe this will go someway towards your answer....

Emmet

---

### Post by petehall on 2005-07-11
[QUOTE=aum11]Thanks for your prompt replies.

Petehall, I have questions about the process You describe of wma to wav and then to mp3.
What will happen to the quality of sound when following this path?
Am I better to try to reload the albums from their cd source?
Is ogg better quality compression than MP3?
What s/w to play and burn?
Ta. O:)[/QUOTE]

1. The WAV will sound identical the WMA, but the MP3 will be of slightly inferior quality. The command I gave you for the WAV-MP3 step uses VBR (variable bitrate) - I find that the quality of MP3s encoded with VBR on it's highest setting is fantastic, so you shouldn't have a problem. Try it with one file and see what you think.

On the off-chance that you don't like the quality of the resultant file, then you have two options - either reload your albums from the CD (remember to use VBR when encoding the MP3s for maximum quality) or you can convert the WMA to WAV and then to FLAC (free lossless audio codec). Neither of these steps involve any loss in sound quality, though FLAC files are enormous - about 3 times the size of an equivalent MP3.

As Emmet said, OGG and MP3 are very similar in terms of quality. The advantage of OGG is that it is an open format, so open-source enthusiasts feel good about themselves when they use it. I use MP3 because iPods won't play OGG files.

2. I use XMMS for playing MP3s, Grip for ripping CDs to MP3, and GnomeBaker for burning CDs (both audio and data). When ripping with Grip, I use the following settings (in Config > Encode):

Encoder executable: /usr/bin/lame
Encoder command line: -h -v -V 0 %w %m
Encode file extension: mp3

Emmet: to "bump" a thread means to add a dummy reply in order to bring it back up to the top of the forum list. People do this when they are concerned that their query has disappeared off the front page before anyone has had a chance to see it. (As an aside, it's generally considered bad etiquette to bump the same query many times in succession.)

---

### Post by emmet on 2005-07-11
Thanks for the clarification. Now I know what *bump* means! Sorry aum11 for sounding a bit peeved then...  :-# 

BTW, I actually think that ogg sounds nicer for the same file size. The problem is finding an 'mp3' player that will also take ogg files. The standard appears to be WMA or MP3 only. 

The quote in my post comes from the vorbis website. I think the crux of the matter is if you take an mp3 and then convert it to an ogg (whether through an intermediate wav or something else), then since mp3 removes information from the file from one place for compression, and ogg removes information from another area for compression, you're going to be left with a file that may be of inferior quality than the original file.

Just my 2cents/pence/etc.

Cheers

Emmet

---

### Post by aum11 on 2005-07-11
Thanks so much guys, that was just what I needed.

---

### Post by petehall on 2005-07-11
[QUOTE=emmet]The quote in my post comes from the vorbis website. I think the crux of the matter is if you take an mp3 and then convert it to an ogg (whether through an intermediate wav or something else), then since mp3 removes information from the file from one place for compression, and ogg removes information from another area for compression, you're going to be left with a file that may be of inferior quality than the original file.[/QUOTE]

But there is a significant overlap in the optimisations made by MP3 and OGG. I have no idea exactly what the figures are, but I'm sure that the amount of data removed when compressing OGG to MP3 is much, much lower than the amount of data removed when performing the original compression. The encoder will basically just not be able to find as many optimisations to perform.

[wikipedia: Audio data compression](http://en.wikipedia.org/wiki/Audio_data_compression#Lossy_compression)

This might be food for an interesting study - take a WAV file and encode it to various lossy formats (perhaps specify a target filesize to ensure a fair test). Then convert these files back to WAVs and "subtract" the waveform from the original to see by how much it differs, and at which frequencies.

Someone's probably already done this exact test.

---

### Post by emmet on 2005-07-11
...and you're right!

[http://www.abde.net/projects/ogg_mp3/](http://www.abde.net/projects/ogg_mp3/) 

Emmet

---

