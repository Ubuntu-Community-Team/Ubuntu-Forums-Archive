---
title: "regular expression help."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by stupidbob307 on 2007-12-25
I am trying to make a regular expression for bracket notation, which is described [here.]("http://humanized.com/weblog/2006/06/30/collaboration_made_simple_with_bracket_notation/")
Really its needs to be three. I am trying to make nano use color syntax for the notation. 

Here's a quick explanation of how it works.


[] deletion
[][] additon
[][][] comment

Example:

the dogs is bestest

the dogs [is][are] best[est] [][][Are you a moron? Jimmy]

[is] deletes the word is
[are] adds the word are
[est] deletes est
[][][Are you a moron? Jimmy] simply a comment from jimmy asking who ever wrote this if they are a moron.


in my ~/.nanorc I have 

color blue "\[[^]]*\]"
color red "\]\[[^]]*\]"
color green "\[\]\[\]\[[^]]*\]"

With this,  "the dogs [is][are] best[est] [][][Are you a moron? Jimmy]"

Comes out like this,   the dogs [COLOR="Blue"][is[/COLOR][COLOR="Red"]][are][/COLOR] best[COLOR="Blue"][est][/COLOR] [COLOR="Lime"][][][Are you a moron? Jimmy][/COLOR]

When it should be   " the dogs [COLOR="Blue"][is][/COLOR][COLOR="Red"][are][/COLOR] best[COLOR="Blue"][est][/COLOR] [COLOR="Lime"][][][Are you a moron? Jimmy][/COLOR]

Can anyone help me?

---

### Post by spiderbatdad on 2007-12-25
backwhack the " ???

---

### Post by blueridgedog on 2007-12-25
color red "\]\[[^]]*\]"

Red fails because it needs to find the last bracket of the blue case.  Can you simply put red first in the load order, so blue will override?

---

### Post by stupidbob307 on 2007-12-25
> **blueridgedog said:**
> color red "\]\[[^]]*\]"

Red fails because it needs to find the last bracket of the blue case.  Can you simply put red first in the load order, so blue will override?

thought of that but it just makes it like this

the dogs [COLOR="Blue"][is][are] [/COLOR]best[COLOR="Blue"][est][/COLOR] [COLOR="Lime"][][][Are you a moron? Jimmy][/COLOR]
 

Thanks for the suggestion though.
Anything else you can think of?

---

### Post by blueridgedog on 2007-12-25
It can be done, but my current mindset is that you are stuck on it due to the need for the red case to pull that first ].  But, I will get my regexp book out in the AM and see if something strikes me.  You may get others that are more conversant in regexp.  I usually get them to work via a very iterative process.

---

### Post by blueridgedog on 2007-12-25
If you change it to:

color red "(\])(\[[^]]*\])"

$1 or the first match will be the ]
$2 or the second match will be the rest

Is there a way in your application to use $2?

($1 and $2 would be populated in a Perl script)

---

### Post by stupidbob307 on 2007-12-25
> **blueridgedog said:**
> If you change it to:

color red "(\])(\[[^]]*\])"

$1 or the first match will be the ]
$2 or the second match will be the rest

Is there a way in your application to use $2?

($1 and $2 would be populated in a Perl script)
 
Your right that would work, but as far as i can see (tested it many different ways). I can't get that value. Too bad not everything has such robust regular expression support as perl.

---

