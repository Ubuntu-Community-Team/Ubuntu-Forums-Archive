---
title: "nano editing help?"
date: 2009-02-03
forum: Arch and derivatives
---

### Post by handy on 2009-02-03
I recently switched editors, dumping leafpad & mousepad for the tabbed beaver.

What I have discovered since, is that really I quite like nano more than any of them, except I haven't worked out how to select chunks of text to delete, copy & paste.

I'm sure that you can do this in nano; I have read the online help, but I could not see how to mark chunks of text larger than one line.

So if any of you do know could you please give me detailed instructions so that I can then dump the beaver & just use nano for all of my text editing in the future.

Thanks :-)

---

### Post by dannytatom on 2009-02-03
Hm, I've been wondering the same for a while and haven't been able to find anything.  As far as I've gotten is using ctrl+k to delete the line you're on.  :/

---

### Post by handy on 2009-02-03
Yeh, that & Ctrl+U to put it back.

I believe that nano is surely able to be a full enough featured text editor for those of us that aren't programming.  Surely someone knows how to mark blocks with nano & will make it known how in this very thread! :-)

I just pulled up the nano man page & I couldn't see a way to mark blocks of text there?

There is the possibility to use the mouse apparently?

Just how useful that is & how you do it I don't know either?

If someone can show me how to mark blocks of text in nano I won't have to go to the trouble of learning how to use vim.

& I really don't need to know how to use vim, if nano will do all that I need.

I'm not looking to start any kind of vim / nano war.  I acknowledge that vim is a far more powerful editor than nano.  It just comes down to how much power an individual needs to edit text.

---

### Post by dannytatom on 2009-02-03
Agreed that vim is overkill for most of my needs, I might learn it eventually though. :P

As for using the mouse, just start nano with 'nano -m'.  What I did was create an alias in my .bashrc like **alias nano='nano -W -m'** - the -W disables wordwrap(it seems to break things every now and then) and the -m enables the mouse.

**Edit:** Forgot you asked how useful it was.  You can't select text for copy/paste (least I can't), but you can click an area and start typing from there.  It's really not all that useful, as holding the down arrow tends to be quicker. :/

---

### Post by Elfy on 2009-02-03
Yea I looked as well at the whole mouse thing - but couldn't work it out

What I do know is that ^K will work on multiple lines if they follow each other and the ^U will paste them all 

mouse control isn't much fun though :(

---

### Post by Elfy on 2009-02-03
or use pico perhaps

installing gpm allows mouse right click in nano it seems as well

---

### Post by dannytatom on 2009-02-03
> **forestpixie said:**
> 
What I do know is that ^K will work on multiple lines if they follow each other and the ^U will paste them all 

Ah, didn't know that. :O

---

### Post by handy on 2009-02-03
I haven't used pico, does it provide the ability to select blocks of text text to cut, copy & paste?

***[Edit:]**  I just had a look in the Arch repo's & when searching for pico I get nano & it states that nano is pico with enhancements.*

---

### Post by Elfy on 2009-02-03
Neither had I until I started looking into this -

[http://www.nwe.ufl.edu/writing/help/others/pico/cut_paste.shtml](http://www.nwe.ufl.edu/writing/help/others/pico/cut_paste.shtml)

but you can use right click menu to copy and paste

---

### Post by sisco311 on 2009-02-03
> **handy said:**
> 
What I have discovered since, is that really I quite like nano more than any of them, except I haven't worked out how to select chunks of text to delete, copy & paste.



M-A (Alt+A) select
M-^ (M-6) copy
^K cut
^U paste

---

### Post by handy on 2009-02-03
> **sisco311 said:**
> M-A (Alt+A) select
M-^ (M-6) copy
^K cut
^U paste

Thanks sisco, I knew you were out there waiting for me to bring you into our lives. :-D

You have just saved me (at least) & some others I'm sure, from having to learn how to use vim.

If I believed in God, I'd get her to bless you. :-)

***[Edit:]** Now, if she was a goddess of My creation, you may not have escaped your salvation for quite some time... :lolflag:*

---

### Post by crimesaucer on 2009-02-03
> **handy said:**
> I recently switched editors, dumping leafpad & mousepad for the tabbed beaver.

What I have discovered since, is that really I quite like nano more than any of them, except I haven't worked out how to select chunks of text to delete, copy & paste.

I'm sure that you can do this in nano; I have read the online help, but I could not see how to mark chunks of text larger than one line.

So if any of you do know could you please give me detailed instructions so that I can then dump the beaver & just use nano for all of my text editing in the future.

Thanks :-)

[http://www.nano-editor.org/](http://www.nano-editor.org/)
[http://www.nano-editor.org/dist/v2.0/nano.html#Command-Line-Options](http://www.nano-editor.org/dist/v2.0/nano.html#Command-Line-Options)

---

### Post by handy on 2009-02-04
Hell crimesaucer, I was really enjoying spreading the easy way to gratuitous self gratification before you came along.

---

### Post by K.Mandla on 2009-02-05
Since we're on the subject, does anyone know if it's possible to wrap text but not insert line breaks at the end? In other words, wrap like a word processor, but the actual file doesn't have "carriage returns" at the end of each line.

Omigosh, I just said "carriage return" for the first time since, like, 1988.

---

### Post by mips on 2009-02-05
> **K.Mandla said:**
> 
Omigosh, I just said "carriage return" for the first time since, like, 1988.

Lol, did you manage to install linux on a typewriter lately? I know you like getting the most out of old hardware but this is pushing it :)

---

### Post by smartboyathome on 2009-02-05
I'd like to just disable nano's wordwrap completely, I have had it mess up several config files which I then had to go back and edit again.

---

### Post by dannytatom on 2009-02-05
You can disable wordwrap by using **nano -W** when starting it, and I also wish there was a real wordwrap. :/

---

### Post by crimesaucer on 2009-02-05
> **handy said:**
> Hell crimesaucer, I was really enjoying spreading the easy way to gratuitous self gratification before you came along.

sorry.

---

### Post by Denestria on 2009-02-05
> **smartboyathome said:**
> I'd like to just disable nano's wordwrap completely, I have had it mess up several config files which I then had to go back and edit again.

Create a .nanorc in your home directory and edit it to say:

set nowrap

Now nano will start every time with word wrap turned off.

---

### Post by smartboyathome on 2009-02-05
> **Denestria said:**
> Create a .nanorc in your home directory and edit it to say:

set nowrap

Now nano will start every time with word wrap turned off.

That doesn't work. Nano just spits out an error and refuses to do it. :(

---

### Post by Denestria on 2009-02-05
That's how I have mine set up.  No errors here.  Have a look at **man nanorc**.

```

$less .nanorc

set const
set tabstospaces
set wordbounds
set nowrap
unset backup

```

---

### Post by smartboyathome on 2009-02-05
> **Denestria said:**
> That's how I have mine set up.  No errors here.  Have a look at **man nanorc**.

```

$less .nanorc

set const
set tabstospaces
set wordbounds
set nowrap
unset backup

```

I know how it is supposed to work, I even set it up with the example nanorc in /etc, but it still doesn't work. It keeps telling me there is no option called nowrap.

EDIT: Had to install nano-wrap from AUR funnily enough to be able to turn off wrapping.

---

### Post by K.Mandla on 2009-02-05
I noticed that too. I am in the habit of tacking on a -w to keep it from wrapping configuration files and screwing things up. Did the package maintainers disable the wrapping option for some reason? nano in Ubuntu and Crux will take that flag normally but the Arch version doesn't.

---

### Post by epictete on 2009-02-05
> **handy said:**
> except I haven't worked out how to select chunks of text to delete, copy & paste.

Hi **Handy** !

Please note that I can do all this with a french azerty keyboard so maybe ^-Maj-6, for example, would be ^-6 on a qwerty keyboard... I don't know!

Selection
*********

Place the cursor at the beginning of the chunk of text to select, press Alt-A or ^-Maj-6 then move the cursor till the end of the selection (that now appears highlighted).

The chunk is memorised until you press Alt-A ou ^-Maj-6.

Cut / Copy / Paste
******************

^K for cutting the selection or
M-Maj-6 for copying the selection
then go to the point where you want to copy and press ^U.

If you have cut the selection by mistake, immediatly press ^U for copy it back in the same location.

Whithout anterior selection, ^K cut and M-MAj-6 copy the entire line; the immediate repetition cut or copy several consecutives lines (they will then be pasted all together by ^U).

Keys
****

^ = Ctrl or [«*Esc*» pressed twice].
«*Meta*» (M) = Alt maintained or «*Esc*» pressed then leaved

---

### Post by epictete on 2009-02-05
I'm sorry: I hadn't seen the answer of **Sisco**!

Leaving the room with the red on my cheeks...:oops:

---

### Post by Denestria on 2009-02-05
This apparently changed recently.  

[http://bbs.archlinux.org/viewtopic.php?id=52824](http://bbs.archlinux.org/viewtopic.php?id=52824)
[http://repos.archlinux.org/viewvc.cgi/nano/repos/core-i686/PKGBUILD?revision=10381&view=markup](http://repos.archlinux.org/viewvc.cgi/nano/repos/core-i686/PKGBUILD?revision=10381&view=markup)

---

### Post by handy on 2009-02-05
> **epictete said:**
> I'm sorry: I hadn't seen the answer of **Sisco**!

Leaving the room with the red on my cheeks...:oops:

No worries, thanks for caring to take the time to make such a comprehensive post. :-)

---

