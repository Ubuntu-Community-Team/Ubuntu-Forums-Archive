---
title: "Open PHP documents"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-24
Hey!

I'm a PHP developer, and I recently downloaded and installed "gphpedit."

I want to open the files.

When I click on a PHP file, I get this error:

```
The filename "admin.tpl.php" indicates that this file is of type "PHP script". The contents of the file indicate that the file is of type "HTML document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
```

I right clicked the file, I went to "Open With" in the properties folder, but I have to do that EACH TIME for EACH file. Is there a fix?

EDIT: It only happens when the file itself has HTML elements in it. A regular PHP fine works fine..

---

### Post by Malibu Illusion on 2007-06-24
The message only occurs when there is a MIME type mismatch, i.e the MIME type of the file is different from what the extension of the file is.

It appears as though the MIME type will remain HTML, even if PHP is used sporadically from within the document itself.  Try declaring this at the very top of your PHP scripts:

```

<?php ?>

```

That seems to ensure the MIME type is set correctly if you're not using PHP right at the top of the document.

---

### Post by alecwh on 2007-06-24
Is there a way around this? I'm making a web application, and that doesn't seem like a great solution.

Thanks though. :D

---

### Post by Malibu Illusion on 2007-06-24
I've never personally encountered this as most scripters I know, including myself, start with large amounts of PHP at the top of the file before they begin any HTML output.

As I said, the problem is its being seen as a HTML MIME type with a .php extension, which is triggering off that alert that you see before you.  I don't really know of how to override this, to be honest with you.  The message is just working as intended upon detection of a mismatch.

Guess this is a free bump on my part to see if anyone does know about this. =)

---

### Post by alecwh on 2007-06-24
Thanks for the background information! :)

However, this is a template file, it's hard to explain, but i I can't start it with a <?php.

---

### Post by Derezo on 2007-10-04
I've got this same problem.
There must be a way to disable this feature of nautilus, no?

This is a very annoying bug. I also use a templating system so not all of my .php files can start with "<?php".

Any help is appreciated. I really don't want to code in a different OS.

---

