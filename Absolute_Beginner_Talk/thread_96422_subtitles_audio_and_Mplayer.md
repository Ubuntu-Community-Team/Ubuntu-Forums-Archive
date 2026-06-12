---
title: "subtitles audio and Mplayer"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Nrvnqsr on 2005-11-28
ok, I'm trying Mplayer for mkv. Plays with no problem, but there is no subtitles active, and no option to change dual audio settings? any ideas how to turn them on? 

Thanks again

---

### Post by ow50 on 2005-11-28
It's all in the man pages.
```
       -aid <ID> (also see -alang)
	      Select  audio channel (MPEG: 0-31, AVI/OGM: 1-99, ASF/RM: 0-127,
	      VOB(AC3): 128-159, VOB(LPCM): 160-191, MPEG-TS 17-8190).	MPlay
	      er prints the available audio IDs when run in verbose (-v) mode.
	      When playing an MPEG-TS stream, MPlayer/MEncoder	will  use  the
	      first program (if present) with the chosen audio stream.

       -alang <language code[,language code,...]> (also see -aid)
	      Specify  a  priority  list of audio languages to use.  Different
	      container formats employ different language codes.  DVDs use ISO
	      639-1  two letter language codes, Matroska and NUT use ISO 639-2
	      three letter language codes while OGM uses a free-form identifi
	      er.   MPlayer prints the available languages when run in verbose
	      (-v) mode.
```
```
       -sid <ID> (also see -slang)
	      Display the subtitle stream specified by <ID>  (0-31).   MPlayer
	      prints the available subtitle IDs when run in verbose (-v) mode.

       -slang <language code[,language code,...]> (also see -sid)
	      Specify a priority list of subtitle languages to use.  Different
	      container formats employ different language codes.  DVDs use ISO
	      639-1 two letter language codes, Matroska uses ISO  639-2  three
	      letter  language	codes  while  OGM uses a free-form identifier.
	      MPlayer prints the available languages when run in verbose  (-v)
	      mode.

	      EXAMPLE:
		 mplayer dvd://1 -slang hu,en
		      Chooses  the Hungarian subtitle track on a DVD and falls
		      back on English if Hungarian is not available.
		 mplayer -slang jpn example.mkv
		      Plays a Matroska file with Japanese subtitles.
```

You can configure a keyboard shortcut for subtitle stream switching, for audio it doesn't work. Also you can configure these in you ~/.mplayer/config, for example I have
```
slang=fi,fin,en,eng
```

---

### Post by Nrvnqsr on 2005-11-28
well, I read abit on the manual and I able to toggle subtitles, one problem solved. But now, I having a hard time understanding the "-aid" and "-alang"

if I understand it right it should be like this?

> 
mplayer -aid


on the conf file

---

### Post by ow50 on 2005-11-29
Starting mplayer from the command line, you could use
```
mplayer -aid 0 movie.mkv
```
or
```
mplayer -alang en,eng movie.mkv
```

Or, in your ~/.mplayer/config you could have the following line.
```
alang=en,eng
```

The stuff in the man pages is command line options. To get the corresponding config file entries, just strip off the leading "-" and add a "=" between the option and its value.

---

### Post by Jazzinghen on 2005-11-30
Thank you for the help. Now I can watch my mkv video files with subtitles!

---

### Post by Nrvnqsr on 2005-11-30
thank you also, I'm able to change audio, thanks again

---

### Post by arkangel on 2005-12-03
Hi People  new to ubunto  but happy  

I installed Mplayer from source  , everything went Ok , i  also downloaded all codecs  for x86 architecture  ,  it works perfectly with  all files i have , but i tried with a dvd  and i can watch the dvd  but there is no soud at all , only with the dvd , palying other format works  Ok , Any idea ?

:)

---

