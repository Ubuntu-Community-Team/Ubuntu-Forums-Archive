---
title: "I broke my Ubuntu"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Toadmund on 2007-03-16
_re; edgy 6.10_
I was downloading some updates when my monitor suddenly showed a bunch of vertical brown lines, nothing else to be seen, then I went and hit the 'reset' button on my tower because I couldn't remedy the problem, then when It started up, instead of a Ubuntu logo, I got what looked like a hockey rink with circles and squares and numbers.

So anyway, I boot in normally; then I can't update.
My sources list is there, but bug buggy comes up instead.

Can I fix my corrupted files using the Live cd?
Here is what seems to be busted:

```
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing cman (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
```

Can I autocorrect this somehow?

Thanks for any help.

---

### Post by STREETURCHINE on 2007-03-16
do the following

        ```
gksudo gedit /etc/apt/apt.conf
```

and add the following line in the file that opens up

       ```
APT::Cache-Limit 12582912
```

save file and close then

       ```
sudo apt-get update
```

ignore gtk warnings and if you still get the same error keep adjusting the number up till it works 

hope it helps

---

### Post by Quillz on 2007-03-16
> **Toadmund said:**
> _re; edgy 6.10_
I was downloading some updates when my monitor suddenly showed a bunch of vertical brown lines, nothing else to be seen, then I went and hit the 'reset' button on my tower because I couldn't remedy the problem, then when It started up, instead of a Ubuntu logo, I got what looked like a hockey rink with circles and squares and numbers.

So anyway, I boot in normally; then I can't update.
My sources list is there, but bug buggy comes up instead.

Can I fix my corrupted files using the Live cd?
Here is what seems to be busted:

```
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing cman (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
```

Can I autocorrect this somehow?

Thanks for any help.
It's almost impossible to break Ubuntu. It sounds like all that happened was your update lists got corrupted, or, at worst, the ubuntu-desktop package. Follow the instructions that were posted above.

If for some reason you need to do an OS reinstall, be sure to back up /home/ so all your data and application preferences are saved.

---

### Post by STREETURCHINE on 2007-03-16
no need to do a reinstall,the fix above will solve the problem
 and you can take the number to 20000000 if need be.

---

### Post by Toadmund on 2007-03-16
> and add the following line in the file that opens up

Code:

APT::Cache-Limit 12582912

What file? The bug buddy file?

or in the terminal?

---

### Post by STREETURCHINE on 2007-03-16
yes open terminal and type or copy and paste

```
gksudo gedit /etc/apt/apt.conf
```

then follow the rest of the top post

no not bug buddy after you type in the first command a file will open it may be empty but just add the line i gave you

       ```
APT::Cache-Limit 12582912
```

---

### Post by Toadmund on 2007-03-16
Yes, I did that, and all I get is bug buddy, so, you mean Yes, put the line that says ```
APT::Cache-Limit 12582912
``` in bug buddy, or put it in terminal?
Sorry if I sound dense, because I am. Too wound up, I did not sleep at all last night.

---

### Post by zekopeko on 2007-03-16
put the lines in gedit which you open with this **command in terminal**. it will open a text editor .

```
gksudo gedit /etc/apt/apt.conf
```

and then just copy&paste this in **gedit** window

```
APT::Cache-Limit 12582912
```

---

### Post by Toadmund on 2007-03-16
> no not bug buddy after you type in the first command a file will open it may be empty but just add the line i gave you
No file, just bug buddy:confused:

---

### Post by STREETURCHINE on 2007-03-16
did you open terminal and type in the command i gave you

---

### Post by Toadmund on 2007-03-16
I did everything, this is all I get, 
```

toad@toad-desktop:~$ gksudo gedit /etc/apt/apt.conf

(gksudo:9489): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:9490): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:9490): Gdk-WARNING **: locale not supported by C library

(gedit:9490): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
toad@toad-desktop:~$
```

no bug buddy now.

---

### Post by Toadmund on 2007-03-16
> **STREETURCHINE said:**
> did you open terminal and type in the command i gave you
No, I copied and pasted it.

---

### Post by seshomaru samma on 2007-03-16
try this :
```
sudo vi /etc/apt/apt.conf
```
this will open the file in the terminal
add the cache line at the end 
then write 
```
:w
```
and press enter

---

### Post by STREETURCHINE on 2007-03-16
did the text editor open


as i said ignore the gtk warnings they mean nothing

---

### Post by Toadmund on 2007-03-16
No text editor, see my terminal in the above post.

---

### Post by Toadmund on 2007-03-16
I think maybe I should just do a re-install, I put my important stuff on dissc.

---

### Post by STREETURCHINE on 2007-03-16
the file will not open in terminal it will be a seperate item 

    so close everything and redo the command in terminal

     ```
gksudo gedit /etc/apt/apt.conf
```


 and look for the file that opens

---

### Post by seshomaru samma on 2007-03-16
I edited my last post , check it out
try using vi instead of gedit in the first command

(if you can't figure out how to save the file in vi , put this command in the terminal```
 vimtutor
``` it will tell you how to use vi- a very unusuall text editor)

---

### Post by STREETURCHINE on 2007-03-16
yes i agree if gedit wont open try vi


and it is in  apt.conf.d

 so it should be    ```
sudo vi /etc/apt/apt.conf.d
```

if this dont work i have anouther way to edit that file,no problen we will get it working again

---

### Post by Toadmund on 2007-03-16
That's a lot of boring reading, how do I just open the vim terminal?

Git it done with.

---

### Post by Toadmund on 2007-03-16
This is too much to absorb right now.
If I can't get it fixed by noon, I'm reinstalling.

Thanks for all your help everyone.
When I break stuff, I break it real good :-\"

---

### Post by STREETURCHINE on 2007-03-16
open vi by typing this in terminal.


    ```
sudo vi /etc/apt/apt.conf.d
```

when it opens copy and past this line in


    ```
APT::Cache-limit "200000000";
```

i am not sure how to save with vi but type in 

    ```
vimtutor
```

it should tell you how to save

---

### Post by dstew on 2007-03-16
Toadmund:

You really should do what streeturchine is suggesting. If you want to learn to use any linux system, you will need to use the terminal. You can re-install, but you will need to use the terminal to do administrative tasks at some point, so why not now?

---

### Post by Toadmund on 2007-03-16
Where in this screenshot do I put the 'APT..." line?

---

### Post by Toadmund on 2007-03-16
> **dstew said:**
> Toadmund:

You really should do what streeturchine is suggesting. If you want to learn to use any linux system, you will need to use the terminal. You can re-install, but you will need to use the terminal to do administrative tasks at some point, so why not now?
Actually, I am learning to use the terminal quite a lot, it's just that things are malfunctioning for me, which is not condusive to a properly functioning terminal.

---

### Post by STREETURCHINE on 2007-03-16
copy and paste it at the end of the text that is there


and to save use     :sav;     type this bit in when you finish do nt paste the sav command

---

### Post by STREETURCHINE on 2007-03-16
and i am sorry but it looks like you got to my post before i corrected a typo so the line to put in will be wrong

---

### Post by Toadmund on 2007-03-16
Does this look normal with all the '[COLOR="RoyalBlue"]@[/COLOR]'s?
(this screenshot stuff is great! I learn all kinds of things when I have computer problems, microsoft taught me a whole lot of stuff!)

---

### Post by STREETURCHINE on 2007-03-16
dont know never had this problem ,
so save it and open terminal and do 

```
sudo apt-get update
```

and see how we go

---

### Post by Toadmund on 2007-03-16
I don't know if it's me or the editor, it's not working. I put in the APT line at the end of 
'.99update-notifier.swp'
then I typed in ':wp'

Then at the end I get:
```
E492: Not an editor command: Cache-limit "200000000";:wp
```


Shall we keep trying, or bury the dead horse?

---

### Post by STREETURCHINE on 2007-03-16
type  :sav;  to save exactly as written

---

### Post by STREETURCHINE on 2007-03-16
its not a dead horse yet it just would have been easier in gedit but since it would not work we will try this if not .we still have a few options to try ,

its better to try to fix than just reinstall it is brocken at the moment so you cant hurt it any more and all this will teach you a bit,

it is getting late here so i will be going to bed soon ,but if we dont get it to work i will post anouther solution in the morning for you to try

---

### Post by esaym on 2007-03-16
Man all this looks complicated even for me.  Ubuntu doesn't have any kind of way to *easily* edit a file?  I know in Kubuntu you just navigate to the file using konqueror and then you right click the file and select "edit as root" and then you type in your password and a text editor opens up and you can see everything.

And yes I know vi :p

---

### Post by Toadmund on 2007-03-16
Don't know if this makes any difference, but I get this message when I first get the desktop screen:
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

The name org.gnome.SettingsDaemon was not provided by any .service files

GNOME will still try to restart the Settings Daemon next time you log in.

Well, It must be due to the fact that all my sources are unopenable?

---

### Post by raul_ on 2007-03-16
I'm sorry to get in the middle but why not use "nano" instead of vi? It's much more simpler to simple file editing...vim is an IDE not a text editor.

---

### Post by STREETURCHINE on 2007-03-16
well i dont know about that ,

so i take it we failed to solve the outher problem

---

### Post by STREETURCHINE on 2007-03-16
> **raul_ said:**
> I'm sorry to get in the middle but why not use "nano" instead of vi? It's much more simpler to simple file editing...vim is an IDE not a text editor.

yes we tried gedit but it would not work and vi was put forward so we tried it,and i have not used nano much so i am not sure on it

---

### Post by raul_ on 2007-03-16
It's pretty straightforward...

```

nano /path/to/the/file

```

edit, Ctrl+X , Y (as in Yes, i want to save the file), and Enter (as in yes, save the file with this name)

---

### Post by Toadmund on 2007-03-16
So I put the previous stuff into nano (sudo nano /blah/blah,) pressed control x, picked 'Y' for yes. 'enter'

Now, it asks:
```
file name to write:
```
If I don't pick something it cancels, what to name it?

---

### Post by raul_ on 2007-03-16
You probably forgot the "sudo" before it :P try with sudo. If no file appears in front of that line just  write the path to the file again and press enter.

---

### Post by Toadmund on 2007-03-16
No, I did put in sudo nano /I forget/wasonlast/page/ (I don't have anywhere to paste this, I'm running on memory, which is bad.)

Then inputed: APT::Cache-limit "200000000";

Try it yourself, it may ask you to name file name to write.

---

### Post by raul_ on 2007-03-16
Ok. When it asks for the file write the file you just opened:

/etc/apt/apt.conf.d

and press enter

---

### Post by Cariboo1938 on 2007-03-16
> **STREETURCHINE said:**
> 
i am not sure how to save with vi 

To save and quit with vi 
press:    "Esc"
Type:     " : "
you'll get the prompt 
:
Type:     " w " stands for write the changes to the file
Type:     " q "  stands for quit the file.

It looks like this at the end of the file
:wq 
and then press "Enter"

---

### Post by Toadmund on 2007-03-16
In nano:
```
 [ Error writing /etc/apt/apt.conf.d: Is a directory ]
```

---

### Post by Toadmund on 2007-03-16
Never mind, I pulled a freshy.
I didn't have much to save on disc that I didn't want to lose.
Thanks to Gnomebaker:)

Oh, and thanks everyone who gave their time to help, much appreciated!

---

