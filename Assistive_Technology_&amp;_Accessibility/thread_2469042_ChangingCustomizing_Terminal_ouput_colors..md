---
title: "Changing/Customizing Terminal ouput colors."
date: 2021-11-17
forum: Assistive Technology &amp; Accessibility
---

### Post by akmartinez12 on 2021-11-17
Hello everyone,

I apologize if this is the wrong area to post this issue and request for help.  If it is an if anyone has the ability to move it to the correct area please do and let me know where to find this post.

I have Glaucoma and retinopathy.  Basically a lot of nerve damage in my eyes but I still have some usable vision.  One of the best ways for me to work is using high contrast and colors that I am comfortable with.

I'm working in the terminal and when I do directory listing in some directories I get some folders that output with a blue text on green background and it's very difficult for me to read the output.  I checked the terminal preferences and played around with them a bit but nothing changes the directories I'm describing.  Can anyone direct me on how to customize/change the colors of these particular types of folders/content?  Below is a screenshot of what I'm describing.

I prefer light text on dark brackgrounds but  if the directory types that do this need the bold background a black text might have enough contrast for me to see what it says.  But any suggestions might help if I can play around with the colors.  


I'm still relatively new to Linux but I learn quick.  I still need detailed instructions though so please don't assume I know what I'm doing.  Thanks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289487&stc=1[/IMG]

---

### Post by MAFoElffen on 2021-11-18
It is fairly easy... I do this. it is sort of hidden, but is there.

What I see in your picture is called gnome-terminal. In the upper right corner, you will see the "venetian blind" looking icon... Select that and it will drop a menu. One of the options is Preferences. Select that menu option. It will open the Preferences panel. In that panel, on the left side of that, you will see menu items for  General, Shortcuts, Profiles, and see the defualt profile of "Unnamed".

Under General, there is an option to select "Theme Variant"... Which there are two basic variants, Light or Dark. That will just change the background to Black or White. You are going to want and need more than just that, so you can ignore those.

You can always change the default Profile (unnamed)... But I always suggest that you keep what is default and create a copy of that default by creating a new Profile to change/modify, while keeping the old default to fall back to if something happens. 

On the Profiles Menu Item, select the "+" icon and it will pop open a sub-menu, to create a new profile... Where you need to come up with a name for a custom profile. It actually says; "Enter name for new profile with default settings:" Once you enter the name, select the "Create" button...

After doing that, the right pane with change to a customization panel... Where you can customize that Profile. The tabs in that panel will be: Text, Colors, Scrolling,  Command and Compatibility. The tabs that I believe will help you are Text and Color.

Under the Text Tab, you can customize the text appearance, cursor and Sound. Your change change fonts, and the size of the fonts. When you select the boxes under the text or background columns, in the bold color, cursor color, highlight color rows... It will popup a color chooser widget for you to change the color of those. 

Under the Colors Tab, the first thing you will want to do is to unselect (uncheck) the first option's checkbox, which says "use colors from system theme". Why? because you are going to want to change that. The second option is a drop down select box that is labeled as "Built-in Schemes:". Under that Drop down are 9 theme options. You can try to use any of the first 8 to see if any of those pre-built themes suit your needs. The ninth option there says "Custom", where you can create your own theme, and choose the colors for.

In the lower half of the panel, there is another drop down select widget, where you can select from the 5 named pre-built Color Pallettes, or select the sixth option, named "Custom" to create your own color pallette.

That may seem a bit daunting at first... To make that easier... You can check a checkbox to unlock/use that row, such as highlight... Select the box in the column, such as Text, let it popup the color chooser widget... Drag that widget out of the way of the panel underneath... And select a color box you want from the displayed Color Pallete shown in the lower panel... And it will update that text option to that color.

After you create a Profile, if you select the Profile name in the left side of the panel, your can modify it. If you select the arrow next to the name, a drop down menu will appear, where you can Clone, Rename, Delete and/or Select that Profile as the Default Profile. You would select "Set as Default" to keep that modified Profile you created as the one you want to use.

Those options should give you enough options to play with and tweak to suit what helps you how you need to adjust for you and your needs. That is probably the most complete tutorial I have written on the hidden customization features of gnome-terminal, gathered from just using it for too many years. I really haven't seen much documentation on this. In older versions, many years ago, these options were not so hidden. That changed when the formal classical menus went away when the Gnome look-and-feel changed.

After using that, you then will have the ability to create multiple Profiles to change things up. I know for me, a "variety" to change to occasionally, is best for me.

That is just for that terminal emulator. there are more advanced terminal emulators, that have similar or other options... It all depends what you want, and how much time you spend in terminal. Terminal Emulators can have "options and features".

---

### Post by KBar on 2021-11-18
Hi and welcome to Ubuntu!

Check [this answer on AskUbuntu]("https://askubuntu.com/a/882154/1044722"). Usually, directories don't have green background, but other-writable directories do. This is what you need to disable or change. 

 > Open up your ~/.bashrc and append the following to the bottom: ```
export LS_COLORS="$LS_COLORS:ow=1;34:tw=1;34:"
```
  save the file and then run 
  ```
source ~/.bashrc
```


---

### Post by KBar on 2021-11-18
This is a follow-up to my previous reply. It will walk you through the process and hopefully help you understand what's going on. You can jump straight to the summary in the end if you feel like it. 

**[SIZE=3]Determining what exactly bash is doing and where colors come from in our listing[/SIZE]**

The program **ls** is parf of the GNU core utilities (**coreutils** package), as confirmed by running:```
dpkg -S /bin/ls
```**coreutils** have complete documentation accessible with```
info coreutils
```
There is a menu on this main page. The tenth item is exactly what we're looking for: _Directory listing_. Use _Tab_ to jump to the next hypertext link and press _Enter_ once the cursor is on _Directory listing_ menu item. It opens another node and right there we can see four items under its menu:

```
* ls invocation::               List directory contents.
* dir invocation::              Briefly ls.
* vdir invocation::             Verbosely ls.
* dircolors invocation::        Color setup for ls, etc.
```

The last one looks really promising! So let's place the cursor on it and jump to its page! No. Hold on. Open a new terminal tab and try entering **dircolors**. Since it is a program, the command will be recognized. Let's look at what it outputs:
```
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:';
export LS_COLORS

```

Aha! A long list of some extensions, some of which are recognizable, and some color values assigned to them. Pay attention to the beginning: there is an assignment statement to an environment variable called LS_COLORS and the variable itself is exported in the end. Now, let's go back to the manual. If you accidentally closed it, fret not. Use this command to invoke that page again:```
info dircolors
```It tells us that there is a sequence of commands to set up the terminal for color output from ls, but how exactly does it happen? We can move around pages with _Pg Up_ and _Pg Dn_ keys. Right in the end, it gives a description of the '--print-database' option:```
&#8216;-p&#8217;
&#8216;--print-database&#8217;
     Print the (compiled-in) default color configuration database.  This
     output is itself a valid configuration file, and is fairly
     descriptive of the possibilities.


```

Let's try it! ```
A very long, multipage output&#8230;
``` Notice how file extensions and their color values are listed one per line and the format is rather strange and may seem arcane. Hmm, maybe pipe it through the less pager?```
dircolors --print-database | less
```Ah, much better! Let's try reading through it. Anything right of a number sign (#) are comments and are not treated as instructions. Again, use arrow keys or _Pg Up_ and _Pg Dn_ to move around. Second batch of comments includes some interesting lines:```
# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

```

[SIZE=3]**Understanding file mode bits**[/SIZE]

It looks like we are going to have to either disable the background color for directories or set it to something else, but how do we do that to directories? They don't have extensions, after all! Luckily, Linux isn't Windows. Everything is a file and every file can be determined by its type.```
drwxrwxrwx
```The very first character _d_ that appears in the long format listing indicates that it is a directory. It is the return of a stat(2) system call. We probably have to look for a line that says "dir(ectory)". Sure enough, there is one:```
DIR 01;34 # directory
```
Let's try to parse it. The first word is self-explanatory: it means the following color codes are assigned to files of type *directory*. From the comments above, we deduce that 01 is the **bold** attribute and 34 is the color [COLOR=#0000ff]blue[/COLOR]. Hmm, that doesn't make any sense. There is no background color set, so how come there is background on our listing? We are going to have to dig deeper. In our directory listing, we had a dozen of directories with identical file mode bits, i.e. _drwxrwxrwx_. Let's read up on this. According to **info** **ls**:

```
&#8216;-l&#8217;
&#8216;--format=long&#8217;
&#8216;--format=verbose&#8217;
     In addition to the name of each file, print the file type, file
     mode bits, number of hard links, owner name, group name, size, and
     timestamp (*note Formatting file timestamps::), normally the
     modification timestamp (the mtime, *note File timestamps::).  Print
     question marks for information that cannot be determined.

 The file type is one of the following characters:

     &#8216;-&#8217;
          regular file
     &#8216;b&#8217;
          block special file
     &#8216;c&#8217;
          character special file
     &#8216;C&#8217;
          high performance (&#8220;contiguous data&#8221;) file
     &#8216;d&#8217;
          directory
```

Earlier we said that the _d_ really stands for *directory* (file type). Well, what about the other nine letters? They are file mode bits. Let's invoke **info** again:```
Basics
* Common options: (coreutils)Common options.
* Coreutils: (coreutils).       Core GNU (file, text, shell) utilities.
* Date input formats: (coreutils)Date input formats.
* Ed: (ed).                     The GNU line editor
* File permissions: (coreutils)File permissions.
                                Access modes.

```

Move your cursor to the _File permissions_ link and press _Enter_. It opens a new document, from which we select _Mode Structure_. There is the explanation:```
The file mode bits have two parts: the &#8220;file permission bits&#8221;, which
control ordinary access to the file, and &#8220;special mode bits&#8221;, which
affect only some files.

   There are three kinds of permissions that a user can have for a file:

  1. permission to read the file.  For directories, this means
     permission to list the contents of the directory.
  2. permission to write to (change) the file.  For directories, this
     means permission to create and remove files in the directory.
  3. permission to execute the file (run it as a program).  For
     directories, this means permission to access files in the
     directory.

   There are three categories of users who may have different
permissions to perform any of the above operations on a file:

  1. the file&#8217;s owner;
  2. other users who are in the file&#8217;s group;
  3. everyone else.


```

[SIZE=3]**Configuring the color setup to our liking**[/SIZE]

The _r_ stands for read permissions (permission to list directory contents), the _w_&#8211;for write permissions (permission to create and remove files in the directory), and the _x_&#8211;for execute permissions (permission to access files in the directory). The first set of the three permissions belong to the file's owner (*u* for short), the second set belongs to other users who are in the file's group (*g* for short) and the third&#8211;to everyone else (*o* for short). We now understand that these directories are other-writable, i.e. the third set includes all permissions and permissions for others (aka everyone else, the world) to write specifically. Well, let's go back to our database now. Scrolling further down a bit we encounter this line with a concise comment that explains it:```
OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
```
34 is for [COLOR=#0000ff]blue[/COLOR] foreground and 42 is for green background. Yes! This is exactly what we were looking to modify. The question is how? With these six simple steps:
[LIST=1]
[*]Save the current configuration file to our home directory with an appropriate name .dircolors. ```
dircolors --print-database > ~/.dircolors
``` 
[*]Open this file with our favorite text editor. 
[*]Edit this line, so that other-writable directories appear in the same colors as ordinary directories, which is 01;34, and keep the comment intact.```
OTHER_WRITABLE 01;34 # dir that is other-writable (o+w) and not sticky
``````
OTHER_WRITABLE 30;42 # this will set foreground color to black, background color remains unchanged, i.e. green
``` 
[*]Put the following lines in your ~/.bashrc (per** info dircolors**).      ```
d=.dircolors
test -r $d && eval "$(dircolors $d)"
``` 
[*]Restart your terminal or source the .bashrc file. ```
source ~/.bashrc
``` 
[*]That's it! Enjoy! 
[/LIST]

Okay, maybe that wasn't six steps at all&#8230;

[B][SIZE=3]See also[/SIZE]

info ls[/B], **info dircolors**, **dir_colors**(5), **console_codes**(4)

Color codes are conformant to ECMA-48/ISO 6429/ANSI X3.64, Set Graphics Rendition section. **console_codes**(4) and [https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters) have the full list of escape codes.

---

### Post by TheFu on 2021-11-18
I disable all colors in my ~/.bashrc (just delete the lines with COLOR), then just set the background and foreground colors when launching xterms (I use xterms).  For example:
```

XTERM_OPTS="-u8 -fs 12 -fa Monospace -sb -fg green -bg black"
xterm $XTERM_OPTS -geometry 78x9+78+0 &
xterm -geometry 80x25+980-72 $XTERM_OPTS -e ssh -X romulus &
...
 
```

There are other xterm commands in my startup file to connect to other systems and place the terminal in an exact location, sized exactly how I prefer.
It also kicks off gnubiff so I know when new email arrives at any accounts.

---

