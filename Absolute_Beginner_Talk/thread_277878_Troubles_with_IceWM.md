---
title: "Troubles with IceWM"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by nietorigineel on 2006-10-15
Hello,

I did a server install of Xubuntu, because i want a very basic system. After that i installed x-windows-system-core, icewm, and gdm, so that i could run the icewm window manager. All fine so far, it works.

My problem: if from the menubar in icewm i select the terminal, it asks for my password, but then nothing happens. So I am kinda stuck now. Also from GDM, the failsafe terminal does not work. How do i get my terminal back? (ctrl-alt-t, which i believe should be the default shortcut in Icewm doesn't work either).

---

### Post by nietorigineel on 2006-10-15
*bump*

---

### Post by IYY on 2006-10-15
The IceWM menu is a plain text one. The easiest way to get a terminal back is  to add the line 
```

prog "XTerm" "xterm" xterm
```

to your ~/.,icewm/toolbar file.

I think your problem is that you (or some program) messed with your x-terminal-emulator script which should be launching gnome-terminal by default.

Here's my /usr/bin/x-terminal-emulator which launches aterm (you can get aterm with sudo aptitude install aterm).

```
#! /usr/bin/perl -w

my $login=0;

while ($opt = shift(@ARGV))
{
    if ($opt eq '-display')
    {
	$ENV{'DISPLAY'} = shift(@ARGV);
    }
    elsif ($opt eq '-name')
    {
	$arg = shift(@ARGV);
	push(@args, "--tclass=$arg", '-t', $arg);
    }
    elsif ($opt eq '-n')
    {
	push(@args, '--icon', shift(@ARGV));
    }
    elsif ($opt eq '-T' || $opt eq '-title')
    {
	push(@args, '-t', shift(@ARGV));
    }
    elsif ($opt eq '-ls')
    {
	$login = 1;
    }
    elsif ($opt eq '+ls')
    {
	$login = 0;
    }
    elsif ($opt eq '-geometry')
    {
	$arg = shift(@ARGV);
	push(@args, "--geometry=$arg");
    }
    elsif ($opt eq '-fn')
    {
	$arg = shift(@ARGV);
	push(@args, "--font=$arg");
    }
    elsif ($opt eq '-fg')
    {
	$arg = shift(@ARGV);
	push(@args, "--foreground=$arg");
    }
    elsif ($opt eq '-bg')
    {
	$arg = shift(@ARGV);
	push(@args, "--background=$arg");
    }
    elsif ($opt eq '-tn')
    {
	$arg = shift(@ARGV);
	push(@args, "--termname=$arg");
    }
    elsif ($opt eq '-e')
    {
	push(@args, '-x', @ARGV);
	last;
    }
    elsif ($opt eq '-h' || $opt eq '--help')
    {
	push(@args, '--help');
    }
}
if ($login == 1)
{
    @args = ('--login', @args);
}
exec('aterm +sb -bg black -fg wheat -fade 80',@args);
```

---

### Post by nietorigineel on 2006-10-15
Thanks for the help. It is however impossible for me to implement your solution, since my problem is I have no terminal to perform all this commands.

Maybe i should have posted a clearer question.

How can i get into a terminal in icewm? The menu link doesn't work, and also the failsafe terminal for the GDM doesn't start up. I used a terminal to install all this, so deep down inside there should be one, only haven't a clue how to get there.

---

### Post by christhemonkey on 2006-10-15
If you type:
<**ctrl**>+<**Alt**>+<**F1**> That should take you to a terminal.

---

### Post by nietorigineel on 2006-10-15
I think i've tried that. (Will again in a sec though). I think this shortcut links to the same program to be found in the menu, which isn't working (which is my problem).

All i did after install of xubuntu server is:

-enable the universe repo's

sudo aptitude update
sudo aptitude x-windows-system-core
sudo aptitude icewm
sudo aptitude gdm

After which i'm in the situation i'm in right now.

Is there a shortcut to kill gdm if you're in there so you get the command line back?

---

### Post by IYY on 2006-10-15
> Is there a shortcut to kill gdm if you're in there so you get the command line back?

Ctrl+Alt+Backspace kills it, but if you just want to go to a console use Ctrl+Alt+F1.

---

### Post by nietorigineel on 2006-10-15
Thanks a lot, ctrl-alt-f1 indeed!

---

