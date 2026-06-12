---
title: "calling a google search"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-28
Hi

I was wondering if someone knew how to open up a specific Google search from the command line. Basically is there a way of referencing any search in a specific url (google.ca/search:<my search>


then from the terminal you could open up your search straight away by the command:

```



firefox google.com/search"<thing to search>"


```

Also I was wondering if there was a way to do this and include Googles "feelings lucky" option, where the first site that is found in the search by google is opened up.

Thanks,

saamon

---

### Post by Cato2 on 2007-10-28
Interesting question - I haven't done this before but thought I would write a simple bash shell function to simplify this.

Paste this into your terminal window - should be all on one line:

function gs() { args="`echo $@ | sed 's/^  *//;s/  *$//;s/  */+/g;'`" ; firefox -new-tab "http://google.com/search?q=$args"; } 

This defines a 'gs' command that you can use as follows - opens a new tab in Firefox, do a 'man firefox' to see the other options such as new window.

   gs ubuntu
   gs ubuntu shell function

As for the 'feeling lucky' part, just do a variant of this function, say gsl, that does the right URL for the feeling lucky search - see what Google generates, and include it within the pattern above.

To make this function appear in all terminal windows (shells), add it to the end of your .bashrc file.

---

### Post by ssaamon on 2007-10-29
thats awesome thanks.

just out of curiosity what does:

sed 's/^ *//;s/ *$//;s/ */+/g;'` do?

also how did you know to goto: search?h=

how could I look up the "feeling lucky" option?

thanks

---

### Post by ssaamon on 2007-10-29
so I didnt mean search?h= I ment search?q=

---

### Post by macogw on 2007-10-29
They knew the search?q= because if you search for anything in Google, that's how it looks in the URL.

Let's see if my sed is good enough to explain this...
ok first, the ` and ` at the beginning and end is telling bash to run that command then send its output back into the larger command that is enveloping it

sed
This tells it to use the program sed, which is a command line text-editor (one where you can't see what it's doing as it does it.  very useful for batch-editting files using a script though)

's/^ *//;s/ *$//;s/ */+/g;'
this is the command being sent to sed

s/^ *//
this means substitute '^ *' for an empty string.  ^ means "at the beginning of the line" and it is followed by a space, so it's searching for a space at the beginning of the line, and in fact any number of spaces at the beginning of the line (that's what the * does) and deleting them, so if you have spaces before what you're searching for, it cuts those spaces out from the beginning to clean it up

the ; means that's the end of that command and so it runs the next after that

s/ *$//
this is substitution again.  it's getting rid of any number of spaces (space followed by *) at the end of the line ($ means end)

s/ */+/g;
this is more substitution.  the spaces between words (no matter how many you put between the words, a large row of spaces will behave like being one space because of the *) are being turned into + since that's how it goes in the URL.  The g at the end means "globally" so if there's more than one word-break, it does it every time it comes up to a set of spaces.

---

### Post by Cato2 on 2007-11-02
Glad you liked it.  For 'feeling lucky', just do a Google search and check what changes in the URL.  Actually this is a little harder but search for 'google feeling lucky url' and someone is sure to have documented this.

---

### Post by Cato2 on 2007-11-12
I just read this [security article]("http://www.heise-security.co.uk/news/98803/from/atom10") that mentions the required URL for 'I'm feeling lucky' searches - just add 'btnl&' in front of the 'q=' part of the alias.

So a new alias for this would be:

function gsl() { args="`echo $@ | sed 's/^ *//;s/ *$//;s/ */+/g;'`" ; firefox -new-tab "http://google.com/search?btnl&q=$args"; }

---

