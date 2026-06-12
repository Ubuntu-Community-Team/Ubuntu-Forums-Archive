---
title: "Find and replace text across Multiple files?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-12-02
Ok, so I have been working on a website for a class for a while, and I need help. I am designing a website for a fictitious company called "The Look". Here is where I need help. Over the multiple html files for the site, I would like to Find every instance of either 'The Look' or 'thelook', except when part of the expression 'thelook.com', and change it to <i>The Look</i> (including the HTML tags) across all of the files (which are all located in the same directory). I have heard that sed may be a possible solution, but it seems far more complicated for this application than I know how to handle. Would anyone be able to help me come up with the code I need??

---

### Post by mdpalow on 2007-12-02
The part that is confusing about your post is.... is this a requirement to show the teacher you can write a script to do this or is this just something you need/want to do to the website pages? 

'cause if it's the latter, why don't you simply do a find/replace and then use .css (common .html practice) to put a keyword there, so if/when you change it in the .css file, it changes it everywhere when the pages are displayed?

---

### Post by brennydoogles on 2007-12-03
> **mdpalow said:**
> The part that is confusing about your post is.... is this a requirement to show the teacher you can write a script to do this or is this just something you need/want to do to the website pages? 

'cause if it's the latter, why don't you simply do a find/replace and then use .css (common .html practice) to put a keyword there, so if/when you change it in the .css file, it changes it everywhere when the pages are displayed?

I think you lost me. I know how to change the css in order to make the selected text formatted however I want, but that is not entirely what I am trying to do. You see, on some pages, the Company is referred to as "The Look", and on others they are referred to as "TheLook" (it was a group project, and this was a miscommunication) It is not just the formatting of the words I want to change, but actually the words themselves. I could manually change it on every page, but I might miss one. That is why I opted for the terminal code. Also, i figure the ability to find and replace from the command line could come in handy some day. Does that make more sense??

---

### Post by teryowen on 2007-12-03
if you know how to program in perl you can do it, perl has great functionality when it comes to something like that, im pertty dusty on this aspect though but heres something i found on the net:

it will open a file and replace all the words "test" with "Change"
```

#! /usr/bin/perl -w

open (IN, "+</path/to/file/test.html");

@file = <IN>;

seek IN,0,0;

foreach $file (@file){
$file =~ s/test/Change/g;
print IN $file;
}
close IN;
```

PS not sure if it actually works but now im intrested so ill test it out and get back to u as soon as i can.

EDIT: Just tested it seems to work fine.

EDIT #2: It is case sensitive home this all helps you out

---

### Post by kidders on 2007-12-14
An alternative might be just to run something like...```
find -iname "*.html" -exec sh -cC '
sed 's/search/replace/' "$1" > "$1".new
' {} {} \;
```That would recursively search for files ending in ".html", replace every occurrence of "search" with "replace" and write the result into a new file with ".new" appended to the end. That way, if you're unhappy with the results, you can scrap the changes with **find -name "*.new" -exec rm {} \;** ... or accept them by doing something similar, with "mv" instead of "rm".

The regular expression you'd need might take a little trial and error ... perhaps that's where perl would come into its own :P ... sed is a little limiting.

---

### Post by dpakatheman on 2008-06-04
#this line copies the .html.new files back to .html files
find -iname ".html.new" | sed 's/.new//' | sh

---

