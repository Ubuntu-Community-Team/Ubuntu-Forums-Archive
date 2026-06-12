---
title: "ls colors dircolors default file types"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Goliath! on 2007-07-15
Maybe this is documented somewhere but I looked hard and couldn't find it in any one place, so I'm posting it.

When I first used Unix (back in the Dark Ages) you could have any colors on your computer screen you wanted - as long as they were black and white (or sometimes green and occassionally *orange*).  So imagine my surprise the first time I went to a bash prompt, typed ls, and got all these funky colors.  What is going on?

Those colors tell what type of file you're looking at.  The colors are defined system wide in a file called /usr/etc/DIR_COLORS, or for a user in ~/.dir_colors.  My out-of-the-box 7.04 system doesn't have either of those files, so there must be an Ubuntu default.

You can find out what the current color settings are by typing dircolors -p.  That will give you a bunch of gobbledygook (letters, numbers, colons, semicolons, etc.).  With the help of man pages, experimentation, and [http://linuxgazette.net/issue01to08/misc/dircolors.txt](http://linuxgazette.net/issue01to08/misc/dircolors.txt) I have translated that default gobbledygook (see below).  I am going to pin this on my wall until I learn it.

Hope some one filnds this useful.

[HTML]File type		Text		Background	Bright
Normal			Default		Default
File			Default		Default
Directory		Blue		Default		Bright
Links			Cyan (grn/blu)	Default		Bright
Pipe			Yellow		Black
Socket			Purple		Default		Bright
Door			Purple		Default		Bright
Block device		Yellow		Black		Bright
Character dev		Yellow		Black		Bright
Orphan link		Red		Black		Bright
setuid			White/gray	Red
setgid			Black		Yellow
Sticky other writable	Black		Green
Other writable		Blue		Green
Sticky bit set		White/gray	Blue
Executable		Green		Default		Bright
*.tar			Red		Default		Bright
*.tgz			Red		Default		Bright
*.arj			Red		Default		Bright
*.taz			Red		Default		Bright
*.lzh			Red		Default		Bright
*.zip			Red		Default		Bright
*.z			Red		Default		Bright
*.Z			Red		Default		Bright
*.gz			Red		Default		Bright
*.bz2			Red		Default		Bright
*.deb			Red		Default		Bright
*.rpm			Red		Default		Bright
*.jar			Red		Default		Bright
*.jpg			Purple		Default		Bright
*.jpeg			Purple		Default		Bright
*.gif			Purple		Default		Bright
*.bmp			Purple		Default		Bright
*.pbm			Purple		Default		Bright
*.pgm			Purple		Default		Bright
*.ppm			Purple		Default		Bright
*.tga			Purple		Default		Bright
*.xbm			Purple		Default		Bright
*.xpm			Purple		Default		Bright
*.tif			Purple		Default		Bright
*.tiff			Purple		Default		Bright
*.png			Purple		Default		Bright
*.mov			Purple		Default		Bright
*.mpg			Purple		Default		Bright
*.mpeg			Purple		Default		Bright
*.avi			Purple		Default		Bright
*.fli			Purple		Default		Bright
*.gl			Purple		Default		Bright
*.dl			Purple		Default		Bright
*.xcf			Purple		Default		Bright
*.xwd			Purple		Default		Bright
*.flac			Purple		Default		Bright
*.mp3			Purple		Default		Bright
*.mpc			Purple		Default		Bright
*.ogg			Purple		Default		Bright
*.wav			Purple		Default		Bright[/HTML]

---

### Post by 5-HT on 2007-07-16
Thanks!

---

