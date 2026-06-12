---
title: "Right click in Thunar"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by aparigraha on 2007-05-26
Greets.
I've been reading up on many posts here without really reaching all the way. Not strange maybe since I'm very new to this.

What I would like to have is a right-click "Sfv-Check" option in Thunar which is applicable to folders (and possibly subfolders) containing *.sfv files.

I got cksfv installed and it all works great in the Terminal using:
```
cksfv -f *.sfv
```

But how do i get that line automatically when Terminal pops up?
If anyone would be so kind to guide me to getting the right command line in Thunar -> Edit -> Configure custom actions

Probably easy as hell, but I will be very greatful.
Thx

---

### Post by ugm6hr on 2007-05-27
I have never used cksfv, so apologies if I haven't understood...

I am assuming that the command *cksfv -f *.sfv * requires the "*" to be a single file name?

If so - it's easy.  
1. Go to Thunar -> Edit -> Configure custom actions.
2. Enter details in "Basic" Tab
Name: Sfv-Check
Description: Sfv-Check
Command: cksfv -f %f
3. Enter details in "Appearance Conditions" tab:
File Pattern: *.sfv
Appears if...: tick "Other file"

Hopefully that works.  If not, we'll try again :p

---

### Post by aparigraha on 2007-05-27
Thx for your reply.
But I think I might have been unclear.
The command I'm looking for is one that opens a Terminal window and there uses the whole command:

cksfv -f *.sfv

where * is looking for any sfv-file.

The right-click option "Open Terminal Here" has the command:

exo-open --working-directory %f --launch TerminalEmulator

Is there maybe a way to add the line "cksfv -f *.sfv" to that somehow?

What am I missing here?

---

### Post by aidanr on 2007-05-27
try 

xterm -hold -e cksfv -f "%d/*.sfv"

---

### Post by aparigraha on 2007-05-27
Thx alot aidanr.
That got me much closer but not all the way.
It seems that  
```
xterm -hold -e cksfv -f "%d/*.sfv"
```
looks for a sfv-file in the parent directory.

Right-clicking in the folder containing the sfv-file and using
```
xterm  -hold -e cksfv -f %F/*.sfv
```
as a custom action command actually does work! Yiihaa. (I removed the "" from above and replaced %d with %F)

But the command for right-clicking a folder and checking any sfv-files it contains...
I just can't get it to work :(
Is it just up to the %letter content?
Anyone?

---

### Post by aidanr on 2007-05-27
if you cd to the directory containing the .sfv's and run cksfv -f *.sfv does that do what you're looking for? if so then you could do:

xterm -hold -e cd "%d" && cksfv -f *.sfv

i don't have cksfv installed so i can't really test it

---

### Post by aparigraha on 2007-05-27
Many thx again aidanr!
But it's still not doing what I want it to do.

xterm -hold -e cd "%d" && cksfv -f *.sfv

just gives me a: xterm: Can't execvp cd: No such file or directory. Don't really know, but is the "cd" command really useful here?

If I use the terminal and cd into the folder containing the sfv-file I can use:
cksfv -f *.sfv

In Thunar I get it working when right-clicking in the dir that contains the sfv-file using the custom command: 
xterm  -hold -e cksfv -f %F/*.sfv
That works just fine. Thx alot!

The same command:
xterm -hold -e cksfv -f %F/*.sfv
also reads the correct sfv-file when right-clickin the whole dir containing the sfv-file, But it can't find any other files to check against the sfv. How do i get xterm to go into the dir before reading it? As it is now, xterm is looking for the matching files in the parent directory.

I'm looking for a way to right-click any dir that contains a sfv-file from its parent directory.
I want xterm and cksfv to go in to the dir that I'm right-clicking and check any sfv-file it contains, and also match the rest of the files.

Again... many thx!

---

### Post by aparigraha on 2007-05-27
Seems i missed an option when using cksfv:

cksfv -r
where -r recursively checks .sfv files in subdirectories

But the problem is not completely solved. If I use it in:
xterm -hold -e cksfv -r
it goes thru ALL subdirectories... not really useful.

Changing to
xterm -hold -e %f cksfv -r
just gives me: Permisson denied
sudo gives me no result what so ever... :(

So I try:
exo-open --working-directory %f --launch TerminalEmulator "cksfv -r"
This seems to work... but there is no -hold option so I can't really see the output.The Terminal window kills itself after the cksfv operation.
Going thru Terminal preferences I see no hold option.

So a way to make xterm move into the right-click directory... or a way to make the Terminal window -hold would be excellent!!
Plz anyone.

---

### Post by SQuark on 2007-06-03
I use something similar for MD5 checksums. I'll try and translate it to SFV, but keep in mind I don't have cksfv installed either, so this is untested.

For "Command:", try this:
```
zenity --info --title="SFV check for %n" --text="$(cksfv -f %f)"
```
Using zenity keeps everything GUI-ish, no need to open a terminal. :)

In the "Appearance Conditions" tab, check "Text Files" and choose the following for "File Pattern:"
```
*.sfv;*.SFV
```

Now right click a .sfv file and try it!

---

### Post by aparigraha on 2007-06-05
Thx alot for your valuable input.
I tried it under commands in Thunar 

```
zenity --info --title="SFV check for %n" --text="$(cksfv -f %f)"
```
Did me no good. A window pops up with a lightbulb :) and an OK-button. And the OK message didn't properly reflect the contents of the sfv-file :( Probably just told me it didn't work properly.

Changing to
```
zenity --info --title="SFV check for %n" --text="$(cksfv **-r**)"
```
and same result.

Also tried it using folders and using different file patterns in thunar.

Might I ask what u use for MD5?

---

### Post by SQuark on 2007-06-05
I installed cksfv to see what was going on and found the problem.
cksf apparently chooses to send its output to stderr rather than stdout.
This code will fix it for you:
```
zenity --info --title="SFV check for %n" --text="<tt>$(cksfv -f %f 2>&1)</tt>"
```
The '2>&1' bit redirects stderr to stdout. I added <tt> and </tt>, because cksfv relies on a monospaced font for its output's layout. You can remove it if you don't like monospace. ;)

For checking all .sfv files inside a directory and its subdirectories, you can use:
```
zenity --info --title="SFV check for %n" --text="<tt>$(cksfv -C %f -r 2>&1)</tt>"
```
(Don't forget to check "Directories" in the "Appearance Conditions" tab.)

I hope this puts an end to your problems! :)

---

### Post by aparigraha on 2007-06-05
A BIG hooooray for your effort. 
```
zenity --info --title="SFV check for %n" --text="<tt>$(cksfv -C %f -r 2>&1)</tt>"
```
This does exactly what I want it to do. I am very greatful... and now I have to learn something new - zenity. Excellent!
THX alot!

---

### Post by SQuark on 2007-06-05
Glad I could help! :)

---

### Post by mrazster on 2007-07-25
This is really helpfull...have been looking for something like this...thnx a bunch.

However I have a little problem with it....when I click the .sfv file I want to have checked....nothing happends...and then after a little while a big message box appears all over screen with the output...looks like this:

[IMG]http://goto.glocalnet.net/mrazster/sfv-checking.png[/IMG]

But this image is croped and scaled ALOT...it is larger then my monitor so I can't se the last lines.

Now I really suck at this...so I have no clue even where to start.
But it would be nice if it where possible to get the message window smaller and mabye with a scrollbar on the side...and also if it would be possible to actually see the "checking" progress.

Is this this possible without to much work...if so..is there anyone willing to help me with this???

---

### Post by SQuark on 2007-07-26
Zenity's info window can't do scrollbars, I think. But Zenity's list window can!
And guess what? It's got the added bonus of showing up while the checking is still in progress!
Unfortunately, it doesn't actually show any sign of activity. But you'll know it's still busy as long as the list is empty. :p
(Actually, I think something should be possible with Zenity's progress window, but I've never gotten it to work the way I want it to. Maybe someone else can shine a light on this?)

Anyway, does this code help you?
```
cksfv -f %f 2>&1 | tail -n +2 | head -c -2 | sed 's/    */\n/' | zenity --list --title "cksfv" --text "Verification results for %f" --column "File" --column "Result" --height=400 --width=500
```
You can change the values for height and width to suit your needs of course.

This will look a little weird when you've got file names with three or more consecutive spaces in them, but I'd say that's pretty rare.

EDIT: Long file names (47+ characters) will also break the look. The following fixes all the problems (I hope), but you may have to change "OK", "No such file or directory" and "different CRC" to their equivalents in your locale.
```
cksfv -f %f 2>&1 | tail -n +2 | head -c -2 | sed 's/ *OK$/\nOK/;s/ *No such file or directory$/\nNo such file or directory/;s/ *different CRC$/\ndifferent CRC/' | zenity --list --title "cksfv" --text "Verification results for %f" --column "File" --column "Result" --height=400 --width=500
```

---

### Post by mrazster on 2007-07-26
> **SQuark said:**
> Zenity's info window can't do scrollbars, I think. But Zenity's list window can!
And guess what? It's got the added bonus of showing up while the checking is still in progress!
Unfortunately, it doesn't actually show any sign of activity. But you'll know it's still busy as long as the list is empty. :p
(Actually, I think something should be possible with Zenity's progress window, but I've never gotten it to work the way I want it to. Maybe someone else can shine a light on this?)

Anyway, does this code help you?
```
cksfv -f %f 2>&1 | tail -n +2 | head -c -2 | sed 's/    */\n/' | zenity --list --title "cksfv" --text "Verification results for %f" --column "File" --column "Result" --height=400 --width=500
```
You can change the values for height and width to suit your needs of course.

This will look a little weird when you've got file names with three or more consecutive spaces in them, but I'd say that's pretty rare.

EDIT: Long file names (47+ characters) will also break the look. The following fixes all the problems (I hope), but you may have to change "OK", "No such file or directory" and "different CRC" to their equivalents in your locale.
```
cksfv -f %f 2>&1 | tail -n +2 | head -c -2 | sed 's/ *OK$/\nOK/;s/ *No such file or directory$/\nNo such file or directory/;s/ *different CRC$/\ndifferent CRC/' | zenity --list --title "cksfv" --text "Verification results for %f" --column "File" --column "Result" --height=400 --width=500
```


Maaaann...this is just beatutiful....works perfectly fine.

You rooock :guitar::guitar::guitar:

---

### Post by SQuark on 2007-07-27
> **mrazster said:**
> You rooock :guitar::guitar::guitar:

Yes, I do a bit, don't I? ;)

I'm jsut glad to help. :)

---

### Post by aparigraha on 2007-07-29
Wow. Thx alot! Great job SQuark!
Check in progress actually works excellent.
But do you get this to work when right-clicking the folder?

I only seem to get it to work when right-clicking the actual .sfv file.
Which Appearance Conditions do you have selected under Thunar Configure Custom Actions?

---

### Post by SQuark on 2007-07-29
Give 'em an inch...  ;)

You'll have to use two seperate actions again. The one I gave above is for .sfv files.
For directories, you can use this one: ```
cksfv -C %f -r 2>&1 | grep -v chdir: | sed 's/\(.*\.sfv\)$/\n\1/;s/ *OK$/\nOK/;s/ *\(No such file or directory\)$/\n\1/;s/ *\(different CRC\)$/\n\1/;s/\(Entering directory:\) /\1\n/;s/--( \(Verifying:\) \(.*\))-*/\1\n\2/;s/\(Everything OK\)./\1\n\n/;s/\(Errors Occurred\)./\1\n\n/;s/^-*$//' | zenity --list --title "cksfv" --text "Verification results for %f" --column "File" --column "Result" --height=400 --width=500
```
(I haven't thoroughly tested this, but it seems to work fine on a few test cases. It's still quite possible I've overlooked a few possibilities, though. Don't hesitate to tell me if that's the case.)
Cheers!

---

### Post by aparigraha on 2007-07-31
well... what can i say.
your efforts keep amazing me!
where is your donate-button? :)

THX!

---

### Post by SQuark on 2007-08-03
> **aparigraha said:**
> 
where is your donate-button? :)
Are you serious? :D

I just like to help people, your thanks is more than enough. :)

---

### Post by ugm6hr on 2007-08-20
> **SQuark said:**
> I use something similar for MD5 checksums.

I've just seen this thread again - and noticed this.  Any chance you could share the command for md5sum with us?

Eternally grateful...

---

### Post by SQuark on 2007-08-20
Sure thing!
```
md5sum -c %F | sed -e 's/: OK$/\nOK/;s/: \(FAILED.*\)/\n\1/' | zenity --list --title "MD5 Checksum" --text="Checking MD5 checksum for:\n%N" --column "File" --column "Result" --height=400 --width=500
```

---

