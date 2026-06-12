---
title: "[SOLVED] Help..How do i remove this using sed?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-03-19
Hi,

I want to remove all of this and don't know how to proceed:
<SCRIPT language="Javascript">
<!--

// FILE ARCHIVED ON 20010105024400 AND RETRIEVED FROM THE
// INTERNET ARCHIVE ON 20071009083456.
// JAVASCRIPT APPENDED BY WAYBACK MACHINE, COPYRIGHT INTERNET ARCHIVE.
// ALL OTHER CONTENT MAY ALSO BE PROTECTED BY COPYRIGHT (17 U.S.C.
// SECTION 108(a)(3)).

   var sWayBackCGI = "http://web.archive.org/web/20010105024400/";

   function xResolveUrl(url) {
      var image = new Image();
      image.src = url;
      return image.src;
   }
   function xLateUrl(aCollection, sProp) {
      var i = 0;
      for(i = 0; i < aCollection.length; i++) {
         if (typeof(aCollection[i][sProp]) == "string") { 
          if (aCollection[i][sProp].indexOf("mailto:") == -1 &&
             aCollection[i][sProp].indexOf("javascript:") == -1) {
            if(aCollection[i][sProp].indexOf("http") == 0) {
                aCollection[i][sProp] = sWayBackCGI + aCollection[i][sProp];
            } else {
                aCollection[i][sProp] = sWayBackCGI + xResolveUrl(aCollection[i][sProp]);
            }
         }
         }
      }
   }

   xLateUrl(document.getElementsByTagName("IMG"),"src");
   xLateUrl(document.getElementsByTagName("A"),"href");
   xLateUrl(document.getElementsByTagName("AREA"),"href");
   xLateUrl(document.getElementsByTagName("OBJECT"),"codebase");
   xLateUrl(document.getElementsByTagName("OBJECT"),"data");
   xLateUrl(document.getElementsByTagName("APPLET"),"codebase");
   xLateUrl(document.getElementsByTagName("APPLET"),"archive");
   xLateUrl(document.getElementsByTagName("EMBED"),"src");
   xLateUrl(document.getElementsByTagName("BODY"),"background");
   var forms = document.getElementsByTagName("FORM");
   if (forms) {
       var j = 0;
       for (j = 0; j < forms.length; j++) {
              f = forms[j];
              if (typeof(f.action)  == "string") {
                 if(typeof(f.method)  == "string") {
                     if(typeof(f.method) != "post") {
                        f.action = sWayBackCGI + f.action;
                     }
                  }
              }
        }
    }


//-->
</SCRIPT>

any ideas?

---

### Post by Athelstan101 on 2008-03-19
You could try this:

```
$ cat file_contining_the_script | tr '\n' ' ' | sed 's/<SCRIPT.*<\/SCRIPT>//'
```

---

### Post by hopelessone on 2008-03-21
thanks..for the pointer...

i want to do a lot of files...

this is what i got so far...

sed -i 's/<SCRIPT*<\/SCRIPT>//g' /home/firebox/Forum4/HTML/*.html

but dosen't work?

---

### Post by Junglizer on 2008-03-21
Sed is a stream editor, so you have to pass it both input and ouptut files specifically so while your previous line is probaly working, it isn't fully changing the files. I wish I could help more but its been a good semester since I used grep/sed/awk together to do anything useful.

---

### Post by ByteJuggler on 2008-03-21
OK, first thing to note is that sed regular expressions operate on *lines* not on the entire file.  This complicates matters slightly.  Basically, you have to consider 2 cases:
1) cases where the regex is on 1 line ,e.g. <script>blahblah blah blah</script>
2) cases where the regex is not on 1 line, in which case you need to jiggery pokery to get it onto one line so sed can match it.  

You do this with the branching/looping support in sed.  Basically, you do a search for 1), if that fails, you join the current and next line, and try again, until you succeed.  You keep doing this, until you're finished. 

Here's one example (using/referring to a bunch of *.txt files I created) that will process a set of files and create a new set with "new." prefixed on the front:

```
for file in $(ls *.txt); do sed -e :loop -e 's/<script>.*<\/script>//g;/script>/N;//bloop'  $file >new.$file  ; done
```

If you're brave, you can make sed edit the files in place (-i switch), but I'd suggest you take a backup first before trying this:

```
sed -i -e :loop -e 's/<script>.*<\/script>//g;/script>/N;//bloop'  *.txt 
```

BTW, I was having some trouble on the "merge lines" part to get sed to recognize <\/script>, so I ended up just searching for "script>" (e.g. the "/script>/N") instead, which works fine.

Hope that helps, and thanks for an interesting question.

---

### Post by hopelessone on 2008-03-22
Hi thanks for the info...

i still can't get it going...??

```
sed -i -e :loop -e 's/<script.*script>//g;/script>/N;//bloop'  /home/firebox/Forum9/HTML/*.html
```

you put a //g;/ and mine was //g' /home/firebox/Forum4/HTML/*.html is that any ehlp?

thanks

---

### Post by ByteJuggler on 2008-03-22
The semicolon is important, it specifies the end of that command, you need to not remove it.  (The bit following, e.g. "/script>" is the next command etc.)  Multiple commands are seperated by semicolons in an inline script like this.

---

### Post by hopelessone on 2008-03-23
OK thanks for the info,

but the script is not working...the file remains unchanged?

i did notice there may be a mistake where you put <script> and a . (dot) after it, the 1st post is <SCRIPT language="Javascript">

i still can't get this going?

what am i doing wrong?

tried varients to get it goin...without luck

```
sed -i -e :loop -e 's/<SCRIPT.*<\/SCRIPT>//g;/SCRIPT>/N;//bloop'  /home/firebox/Forum9/HTML/000033.html
sed -i -e :loop -e 's/<SCRIPT*<\/SCRIPT>//g;/SCRIPT>/N;//bloop'  /home/firebox/Forum9/HTML/000033.html
sed -i -e :loop -e 's/<SCRIPT language="Javascript">.*<\/SCRIPT>//g;/SCRIPT>/N;//bloop'  /home/firebox/Forum9/HTML/000033.html
sed -i -e :loop -e 's/<SCRIPT language="Javascript">*<\/SCRIPT>//g;/SCRIPT>/N;//bloop'  /home/firebox/Forum9/HTML/000033.html
```

Attached file for testing...

thanks

---

### Post by ByteJuggler on 2008-03-23
Hey,

OK, there's something odd going on, I couldn't get it working either for some strange reason on your file.  :confused:

However, having slept over it a night or 2, it occurred to me that what I suggested is probably not the simplest way to solve the problem anyway -- simply deleting the lines we don't want is easier to write and to understand (and happens to work without fuss or bother):

```
sed -i '/<SCRIPT/,/<\/SCRIPT>/d' test.txt
```

What that's doing is to say, from the line containing "<SCRIPT", to the line containing "</SCRIPT>", delete ("d") the lines found.

That seems to achieve mostly the same goal, although if you have more text on the lines with Script tags on, that text will obviously also be deleted.

---

### Post by hopelessone on 2008-03-23
I cannot thank you enough for the time and effort you put into this...

i'm like you having slept over it a night or 2 my mind too ticks while sleeping....

A big THANKS... !!!!

solved it... :KS

---

