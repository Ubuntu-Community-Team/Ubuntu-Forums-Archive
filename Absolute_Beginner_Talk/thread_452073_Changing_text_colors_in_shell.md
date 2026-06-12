---
title: "Changing text colors in shell"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-05-22
I want to change text colors for different types of files in the shell.  Example, directories show up as dark blue and images show up as light purple.  Is it possible because I did not see the option under the color tab in current profile.  

[IMG]http://zune-downloadz.com/textcolors.png[/IMG]

As you can see the light blue and green text is hard to read.  I have played around with background colors and that has not helped.

Thanks

---

### Post by pmg on 2007-05-22
Look at the man pages for **dircolors** and **dir_colors**.  e.g.:  ```
man dir_colors
```

---

### Post by wormser on 2007-05-22
Thanks

---

### Post by Martin on 2007-05-22
If you just want to change the background colours, text type,colour etc.
Open a terminal choose Edit then Profiles, choose the profile you wish to change probably Defaults, choose the Edit button on the right and edit away

---

### Post by graigsmith on 2007-05-22
hey, i got a question, you know tab autocompletion. where you can type something hit tab in the terminal and get it to guess at the thing you are typing?  is it possible that you can make it guess things when you have typed the incorrect case on something.

lets say you are trying to cd into the directory called Capital.  it would be cool if you could type cap<tab> and it would fix the case for you and allow you to get into the capital folder without using the shift key.  is there any way to config this? or not?

---

### Post by wormser on 2007-05-23
> **Martin said:**
> If you just want to change the background colours, text type,colour etc.
Open a terminal choose Edit then Profiles, choose the profile you wish to change probably Defaults, choose the Edit button on the right and edit away

There are no options there to change directories to a different color.  I know you can change the background there and the text.  But you cannot change the color of directories, image files, ...  Look at the picture in the top post.  See the green and light blue file name.  That is what I want to change because it is hard to read.  

I am still reading about dir_colors and have not figured it out yet.

---

### Post by Martin on 2007-05-23
Interesting I took a look in /usr/bin/dircolors. Those look like filetype listings and color codes.Have a play in there and post here if it works.

---

### Post by Martin on 2007-05-23
[http://www.issociate.de/board/post/249372/BASH:_how_to_change_the_default_file_type_color.html](http://www.issociate.de/board/post/249372/BASH:_how_to_change_the_default_file_type_color.html). Some of the dir names don't match but the method looks plausible

---

### Post by wormser on 2007-05-23
I found a nice [tutorial]("http://ubuntuforums.org/showthread.php?t=41538").

---

