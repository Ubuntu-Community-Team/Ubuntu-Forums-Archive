---
title: "HTML for &quot;index&quot; page of server"
date: 2009-08-21
forum: Art &amp; Design
---

### Post by PurposeOfReason on 2009-08-21
I'm looking for a way to make this page of my server look better. Really I'd like it to have two rows instead of one, no icons, anything but the file name, and follow a theme like this where there is always a navigation tab at the top.

[http://www.directoryadmin.info](http://www.directoryadmin.info)

---

### Post by Nevon on 2009-08-21
> **PurposeOfReason said:**
> I'm looking for a way to make this page of my server look better. Really I'd like it to have two rows instead of one, no icons, anything but the file name, and follow a theme like this where there is always a navigation tab at the top.

[http://www.directoryadmin.info](http://www.directoryadmin.info)

Well, then you're going to have to make a custom index page where you list all directories as an unordered list, and then style that list. Getting two rows will be a little bit difficult though, as there's really no great way to handle multi-column lists. Here's an article discussing it: [http://www.alistapart.com/articles/multicolumnlists/](http://www.alistapart.com/articles/multicolumnlists/)

Edit: Nevermind. Old article. [http://www.alistapart.com/articles/css3multicolumn](http://www.alistapart.com/articles/css3multicolumn)

---

### Post by PurposeOfReason on 2009-08-21
I really wouldn't want to have to add each folder as it would be a right pain. I was thinking about using PHP for that as shown here:
[http://snipplr.com/view/833/](http://snipplr.com/view/833/)

Finished
[s]I'm just not sure how to apply it. I put it in the index.html folder for that directory, but it just shows a few lines of code where the output should be. I did test the php and it does work.[/s]

 Then, would it also be be possible to have a higher level folder reference the index.html of the previous level? The folder structure is like so
/var/www/movies/some.movie.folder/avi.mkv.files

It would be much easier to have the final directory (avi.mkv.files) just use the index.html file for some.movie.folder including the php script.

---

### Post by Nevon on 2009-08-22
> **PurposeOfReason said:**
> Then, would it also be be possible to have a higher level folder reference the index.html of the previous level? The folder structure is like so
/var/www/movies/some.movie.folder/avi.mkv.files

It would be much easier to have the final directory (avi.mkv.files) just use the index.html file for some.movie.folder including the php script.

If I understand you correctly, you mean you want to have a navigation as such:
var &#8594; www &#8594; movies &#8594; some.movie.folder 
and then just be able to click on one of those folders and be taken there automatically? 

That's called a breadcrumb navigation, and should probably not be too hard to implement in PHP. Try googling it.

---

### Post by PurposeOfReason on 2009-08-22
Kind of, I'm able to navigate just fine. It's more that say we're in the directory /var/www/movies. I have that set up all nice and can get to any folder from in there just fine. The problem is once I go into one of those folders it does not use the html/css from the page you were just at, which of course it shouldn't because there is nothing telling it to. I'm looking for a way to make it so that it backtracks to know what code to use as it would be a really big hassle to copy the .php and .css files to all the hundreds of folders (not to mention a waste of space). I would just soft link it, the php for the page has a reference to the directory it is in so that it lists those files. If I were to just link it to some.movie.folder, the page would still just display the directory for /var/www/movies.

If that made any sense.

---

### Post by maruchan on 2009-08-22
Like this? [http://www.evoluted.net/community/code/directorylisting.php](http://www.evoluted.net/community/code/directorylisting.php)

---

### Post by PurposeOfReason on 2009-08-22
No, I think screens will help to explain. Here we are at the main folder, everything is working just fine. Now if I go one folder deeper, it is just default. I'd like it to be the same, but the only say I can think of doing that is to put my index.php and default.css files in each sub directory (the one that looks default). The problem with doing this is part of the index.php has a line that says:
```
$path = "/var/www/movies/"'
```so for it to work I would need to change that to /var/www/movies/007, but for each folder which I have hundreds of. I'd really like it to be modified so it just followed the folder structure.

I'm not sure if any of this is even possible. I don't know much about php or html.

---

### Post by Nevon on 2009-08-23
That shouldn't be too hard. Just don't ever leave the index page, but instead have PHP list the files inside the next folder, etc.

---

