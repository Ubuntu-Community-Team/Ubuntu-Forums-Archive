---
title: "Manipulate a txt file"
date: 2013-04-02
forum: Any Other OS
---

### Post by Si1414 on 2013-04-02
I have the following txt file:

```
source.txt:
<a href="**/gp/product/bold.jsp?tp=&add=B007OZNZG0**"><a href="https://www.amazon.com/gp/product/utility/edit-one-click-pref.html?ie=UTF8&query=*entries*%3D0%2C*Version*%3D1&returnPath=%2Fgp%2Fproduct%2FB007OZNZG0" id="oneClickSignInLinkID">Sign in</a> to turn on 1-Click ordering.
<tr><a href="**/gp/product/****bold.jsp?tp=&add=****B007OZAJSDH**"><td align="right" style="font-weight:....
...



```which is essentially bunch of junks with some links that have "**bold.jsp**" (bolded above).

What I want to do is to:
1- extract the bold parts (which have **bold.jsp**) and write them to a new txt file (each in a separate line)
2- add "http:www.amazon.com" to the beginning of each line

So the output would be:

```
output.txt:
http:www.amazon.com**/gp/product/bold.jsp?tp=&add=B007OZNZG0**
http:www.amazon.com**/gp/product/****bold.jsp?tp=&add=**[B]B007OZAJSDH

[/B]
```
I am using Cygwin on Windows.

Thank you for your help.

---

### Post by schragge on 2013-04-02
```

awk -F'"' -vRS='<a[ \t\n]+href="' '$1~/bold\.jsp/{sub(/^\//,"http://www.amazon.com/");print $1}' source.txt

```

---

### Post by Si1414 on 2013-04-02
Thank You. Great help..
How to put each link in a separate line?
When I use the following code, it writes all links after each other and not in separate lines:

```
(awk -F'"' -vRS='<a[ \t\n]+href="' 'NR>1{sub(/^\//,"http://www.amazon.com/"); print $1}' source.txt) >output.txt
```

---

### Post by schragge on 2013-04-02
Strange. On my system, it puts each link on its own line. What awk implementation Cygwin uses? gawk? You could try to redirect the output from inside awk:
```
awk -F'"' -vRS='<a[ \t\n]+href="' '$1~/bold\.jsp/{sub(/^\//,"http://www.amazon.com/"); print$1[COLOR=red]>"output.txt"[/COLOR]}' source.txt

``` or explicitly set the ORS variable:
```
awk -F'"' -vRS='<a[ \t\n]+href="' [COLOR=red]-vORS='\r\n'[/COLOR] '$1~/bold\.jsp/{sub(/^\//,"http://www.amazon.com/");print$1}' source.txt
```
or both.

TBH, I suspect it _does_ print links on separate lines, but ends each line with LF alone (Unix convention), not with CR+LF (Windows convention), thus ORS='\r\n' above. Or you can open *output.txt* in an editor that understands the Unix convention like [Notepad++]("http://notepad-plus-plus.org/"). Alternatively, convert the file with [unix2dos]("http://manpages.ubuntu.com/manpages/precise/en/man1/unix2dos.1.html").

BTW, I've edited my post and changed the code to only select lines that contain *bold.jsp*.

---

### Post by Si1414 on 2013-04-02
Thanks again. The second code works perfect!

---

