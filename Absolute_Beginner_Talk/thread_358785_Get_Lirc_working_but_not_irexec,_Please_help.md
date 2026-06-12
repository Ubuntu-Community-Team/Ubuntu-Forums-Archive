---
title: "Get Lirc working but not irexec, Please help"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Shawn Dineley on 2007-02-11
Hello

    I finally got Lirc working. My remote works in mplayer as setup in my lircrc . But I aslo put a command in the lircrc file to start mplayer with irexec. But it doesn't work. I've also tried another commands to start another programs. That I've found on the forum. But none work. What I'm I doing wrong. (and yes I started irexec in terminal)

Here's my Lircrc

# MPLAYER ======================================|
begin mplayer
begin 
    prog = irexec
    button = TIVO
    mode = mplayer
    config = /usr/bin/mplayer
end
begin
    prog = mplayer
    button = PLAY
    config = pause
end
begin
    prog = mplayer
    button = REWIND
    config = seek -10
end
begin
	prog = mplayer
	button = FORWARD
	config = seek 10
	repeat = 1
end
begin
	prog = mplayer
	button = WINDOW
	config = vo_fullscreen
end
begin
	prog = mplayer
	button = CHAN_UP
	config = volume 1
	repeat = 1
end
begin
	prog = mplayer
	button = CHAN_DOWN
	config = volume -1
	repeat = 1
end
begin
    button = TIVO
    prog = mplayer
    config = esc
end

begin
    button = THUMB_DOWN
    prog = mplayer
    config = pt_step -1
    repeat = 1
end
begin
    button = THUMB_UP
    prog = mplayer
    config = pt_step 1
    repeat = 1
end
end mplayer

---

