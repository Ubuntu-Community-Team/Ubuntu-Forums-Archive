---
title: "Apache server issues"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mac173 on 2007-06-04
Ok, I have installed the Apache 2 server, and can start the server. I can display the default "It Works" page, so I know the server is working. 

My problem is, I have changed the default file to hold the HTML for a web page I started, but the server continues to display the default page!

I have tried changing all of these files, but get the same default "It Works" page still.

    /etc/apache2-default/index.html
    /var/www/apache2-default/index.html
    /etc/apache2-default/home.html  (my name for the first page of my web page)

I don't seem to be able to get the server to find the web page. I have read several tutorials on the Apache server, none of which address this. 

Can someone please help me as to what directory to put the files in, and how do I set up for multiple pages for my web page? I have a home page, and 5 other pages with references to each other.

---

### Post by dfreer on 2007-06-04
I generally end up deleting /var/www/apache2-default/, and the default web page root is /var/www/ so any index.html file you put in there should be loaded up when you browse to [http://localhost](http://localhost)

As for multiple pages, simply have the index.html link to them in some way... I don't see what your problem is here?

---

### Post by mac173 on 2007-06-04
Ok, let me see if I am getting this right...

Set my home page in /var/www/index.html

Then set my other pages in /var/www/family.html 
and /var/www/links.html and so on

Is that correct?

Also, /var/www/apache2-default is a directory. There are several image files in the directory that I would not want to delete, so where do I move them to, and how? Then, what is the command to delete that directory?

Sorry, I know this sounds pretty simple to you, but I am many years from when I last used command line for anything.

---

### Post by dfreer on 2007-06-04
Yep, the above file locations look right. Then, when you are making your link, you can do it with either: a href="family.html" or a href="http://localhost_or_your_domain_name_here/family.html

Yes it is a directory, if you want to keep the files you could either just leave the directory on there or move them up a level into your main website, then delete the directory. To delete a directory, with or without files/folders in it:
```
rm -Rv mydirectoryname
```
You may need to run that command with sudo depending on what the permissions are of the folder.

To copy files (examples):
```
cp -v myimage.jpg /var/www/
cp -v *.png ../    # takes all files with the extension .png and copies them in the above directory
```

To move files (examples):
```
mv -v myimage.jpg /var/www/images/
mv -v *.png ../images/   # same as as the cp command but deletes the original file after the move, and puts them in the above directory, and then in a sub-directory names images
```

Try to think of your website [http://localhost_or_your_domain_name](http://localhost_or_your_domain_name) being equal to /var/www. Anything you put in there is your website. Any folder you create will be accessible from the WWW, such as [http://localhost/familypics/](http://localhost/familypics/).
You can put the images or webpages anywhere in /var/www/ you want, in any folder you want (you can do even more stuff but that's for another time), the important thing to realize is if you create an index.html page, the server will automatically load that page when you browse to the site/folder (this can be changed to be any file). Another thing is when you link to sites/stuff, any kind of link, you'll need to know where that file is in relation to the file you are working on. So let's say you have this website:

```

/
 home/
      $USER/
            coolpic.png
 var/
     www/
          index.html
          family.html
          images/
                  image01.jpg
                  image02.jpg
          pictures.html  

```

If you want image01.jpg to appear on pictures.html, you would link to it thusly: src="images/image01.jpg"
Index.html could have a link to pictures.html like so: href="http://localhost/pictures.html"
but you won't be able to call coolpic.png into the website unless you copy it, or perform some voodoo magic (ok there's several other ways but that's enough for now)

---

### Post by mac173 on 2007-06-04
Thanks, that helps a bunch. I just changed names on some files, and it works. The links need some changes, but I changed two and they work great. Now I just gotta get to work in Scream and translate this archaic site to CSS.....

---

