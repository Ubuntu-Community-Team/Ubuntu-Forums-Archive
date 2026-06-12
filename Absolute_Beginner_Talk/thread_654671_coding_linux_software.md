---
title: "coding linux software"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by shadows123 on 2007-12-31
Well..
I don't know.. Just makes me curious :P
Which software do you guys use to code linux apps?
And how do you know which file extension it must have LOL.. xD
I'm used to use windows too much i think :P
Thanks to answer!
Also,
how can you submit your software to synaptic or add/remove applications thingy?
I plan on coding something :p
Thanks!
edit: anyone uses kommander? it looks like visual basic lol :p

---

### Post by dburnett77 on 2007-12-31
Word of mouth.  JADE and Eclipse are great at cross compiling several languages.

if you want to submit something, start with your friends, and make sure it's operative.

In great demand these days there are two facets:

Entertaining/distracting, and the converse of seperate tools.

Depending on your knowledge base, go for one of these.  Of course, I'd start with gcc, gfortran or something.

try gnu.org.  They've got great examples.

---

### Post by raul_ on 2007-12-31
vim FTW xD

now seriously:
you only need a text editor and a compiler for any language (well actually java needs the virtual machine) . file extensions aren't used in linux. They're just a convention for the user. you could rename "whatever.pdf" to "wtf" and it would still open as a pdf.

To make sure other people can install it, first you need to create your own repository, or find a 3rd party repository that you can submit your program to. Then people have to add that repository to their sources. Take one step at a time ;)

---

### Post by LaRoza on 2007-12-31
> **shadows123 said:**
> Well..
I don't know.. Just makes me curious :P
Which software do you guys use to code linux apps?
And how do you know which file extension it must have LOL.. xD


I use an editor (usually Kate now, but Vim, Kwrite and Gedit too)

It depends on the langauge and compiler.

C == .c
C header == .h
C++ == .cpp
C++ header == .hpp
Fortran 77 == .f
Fortran 90 == .f90
Java == .java (the javac compiler requires this)
Python == .py
Perl == .pl
Ruby == .rb
PHP == .php, .php5
LISP == .lisp (original, eh?)

For the compilers I use, gcc and such, there are special file extensions for certain files. Some file extensions indicate certain files should be preprocessed and such.

If you need help programming in Linux, see my wikis (the second is for Ubuntu and is linked to in my wiki in my sig)

If you need programming assistance, see the Programming Talk forum (under "Development and Programming")

---

### Post by shadows123 on 2007-12-31
Cool i see.
my app will be: appftw!!.wtf??? xD just kidding lol..
idk.. it's new for me :p
only thing i don't like that much is msn clients for ubuntu lol.. but ubuntu is gud.. :p
Hmm..
php is web lang lol.. can u code in php to make an app for linux?? :O!!
that'd be awesome lol.. i can code php already :p
but i'm ready to learn things :p lol
LaRoza, nice wiki!! :p

---

### Post by shadows123 on 2007-12-31
Oh and i have a question :p
can you go to add/remove software in apps?
search for mathgenius.. it's a calculator..
you guys have any idea with what it's made?
Thanks :)

---

### Post by LaRoza on 2007-12-31
> **shadows123 said:**
> 
php is web lang lol.. can u code in php to make an app for linux?? :O!!
that'd be awesome lol.. i can code php already :p
but i'm ready to learn things :p lol
LaRoza, nice wiki!! :p

[http://www.devx.com/opensource/Article/21235/0](http://www.devx.com/opensource/Article/21235/0) yes, PHP can be used in many ways.

[http://gtk.php.net/](http://gtk.php.net/)

[http://phpdiscovery.com/category/desktop-programming/](http://phpdiscovery.com/category/desktop-programming/)

[http://devzone.zend.com/article/2654-Developing-Desktop-Applications-in-PHP-for-Beginners](http://devzone.zend.com/article/2654-Developing-Desktop-Applications-in-PHP-for-Beginners).

---

### Post by LaRoza on 2007-12-31
> **shadows123 said:**
> Oh and i have a question :p
can you go to add/remove software in apps?
search for mathgenius.. it's a calculator..
you guys have any idea with what it's made?
Thanks :)

[http://www.5z.com/jirka/genius.html](http://www.5z.com/jirka/genius.html)

That?

It is written in C.

---

### Post by shadows123 on 2007-12-31
I see..
And..
sorry maybe i posted in wrong section.. but..
i make a php file with easy php code like:
```

<?php
$xD == "lool";
echo $xD;
if ($xD == "lool")
{
echo "it's lool!";
}
else
{
echo "It's not lool...";
}

?>

```
ok?
i open it, but it opens with text pad xD..
how do i have to do it that it's an app? xD 
lol Thanks..
really a newb lol.

---

### Post by shadows123 on 2007-12-31
can anyone show me a phpgtk app?
So i know what it looks like lol :P.
Thanks..

---

### Post by LaRoza on 2007-12-31
> **shadows123 said:**
> can anyone show me a phpgtk app?
So i know what it looks like lol :P.
Thanks..
[php]
<?PHP
if (!class_exists('gtk')) {
    die("Please load the php-gtk2 module in your php.ini\r\n");
} 
$wnd = new GtkWindow();
$wnd->set_title('Hello world');
$wnd->connect_simple('destroy', array('gtk', 'main_quit')); 
$lblHello = new GtkLabel("hello world");
$wnd->add($lblHello); 
$wnd->show_all();
Gtk::main();
?>
[/php]

[php]
#! /usr/bin/php -q
<?php
    echo "Hello world\n";
?>

[/php]

PHP-CLI might be better to start with.

[http://www.php.net/features.commandline](http://www.php.net/features.commandline)

My wiki has a new page for PHP for the desktop, [http://laroza.pbwiki.com/PhpDesktop](http://laroza.pbwiki.com/PhpDesktop)

---

### Post by shadows123 on 2007-12-31
ah ic..
so you should have php installed for it to work :p
so i guess c or c++ & etc is better..
So another thing.. i guess this is my last question lol :p
i made something with the application: kommander dialog editor
i saved it.. it saved as .kmdr
now what do i have to do so people can use it?
[contents of kmdr file - was just a test lol]
```

<!DOCTYPE UI><UI version="3.0" stdsetdef="1">
<class>Form1</class>
<widget class="Dialog">
    <property name="name">
        <cstring>Form1</cstring>
    </property>
    <property name="geometry">
        <rect>
            <x>0</x>
            <y>0</y>
            <width>594</width>
            <height>480</height>
        </rect>
    </property>
    <property name="caption">
        <string>Form1</string>
    </property>
    <widget class="TextEdit">
        <property name="name">
            <cstring>TextEdit2</cstring>
        </property>
        <property name="geometry">
            <rect>
                <x>110</x>
                <y>50</y>
                <width>380</width>
                <height>72</height>
            </rect>
        </property>
        <property name="text">
            <string>Put your text here to e-Mail us!</string>
        </property>
    </widget>
    <widget class="CloseButton">
        <property name="name">
            <cstring>CloseButton1</cstring>
        </property>
        <property name="geometry">
            <rect>
                <x>180</x>
                <y>380</y>
                <width>241</width>
                <height>21</height>
            </rect>
        </property>
        <property name="text">
            <string>I hate it! &amp;Close this ASAP!</string>
        </property>
    </widget>
    <widget class="ExecButton">
        <property name="name">
            <cstring>ExecButton1</cstring>
        </property>
        <property name="geometry">
            <rect>
                <x>210</x>
                <y>130</y>
                <width>150</width>
                <height>20</height>
            </rect>
        </property>
        <property name="text">
            <string>Send e-&amp;Mail</string>
        </property>
        <property name="on">
            <bool>false</bool>
        </property>
        <property name="associations" stdset="0">
            <stringlist>
                <string>@TextEdit2.settext(Error! E-Mail not sent!!)
@TextBrowser1.settext(It seems were having problem with your internet connection we cannot connect to the internet to send the email.)</string>
            </stringlist>
        </property>
        <property name="whatsThis" stdset="0">
            <string>Submit your suggestion for us!</string>
            <comment>Submit your suggestion for us!</comment>
        </property>
    </widget>
    <widget class="TextBrowser">
        <property name="name">
            <cstring>TextBrowser1</cstring>
        </property>
        <property name="geometry">
            <rect>
                <x>100</x>
                <y>170</y>
                <width>381</width>
                <height>181</height>
            </rect>
        </property>
        <property name="text">
            <string>Information bar.</string>
        </property>
        <property name="associations" stdset="0">
            <stringlist>
                <string>@Form1.settext(TEST?)</string>
            </stringlist>
        </property>
    </widget>
</widget>
<layoutdefaults spacing="6" margin="11"/>
</UI>

```

---

