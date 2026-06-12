---
title: "[function.move-uploaded-file]: failed to open stream: Permission denied in"
date: 2007-03-07
forum: Arkansas Team - US
---

### Post by uamusa on 2007-03-07
Trying to implement and Upload form on my Web Server:

**upload.hmtl  :**

<form enctype="multipart/form-data" action="upload.php" method="POST">
Please choose a file: <input name="uploaded" type="file" /><br />
<input type="submit" value="Upload" />
</form> 

**upload.php  :**
<?php 
$currentdir = getcwd();

$target = $currentdir . "/upload/"; 
$target = $target . basename( $_FILES['uploaded']['name']) ; 
echo "Temp Location: $target_path<br>";
$temploc=$_FILES['uploadedfile']['tmp_name'];
echo "Temploc: $temploc<br>";

$ok=1; 

//This is our size condition 
if ($uploaded_size > 350000) 
{ 
echo "Your file is too large.<br>"; 
$ok=0; 
} 

//This is our limit file type condition 
if ($uploaded_type =="text/php") 
{ 
echo "No PHP files<br>"; 
$ok=0; 
} 

//Here we check that $ok was not set to 0 by an error 
if ($ok==0) 
{ 
Echo "Sorry your file was not uploaded"; 
} 

//If everything is ok we try to upload it 
else 
{ 
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))   //**THIS IS LINE 43**
{ 
echo "The file ". 
basename( $_FILES['uploadedfile']['name']). " has been uploaded"; 
} 
else 
{ 
echo "Sorry, there was a problem uploading your file."; 
} 
} 
?>


**What you get when you attempt to use the upload form  :**

Warning: move_uploaded_file(/home/chris/public_html/upload/Caleb.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /home/chris/public_html/upload.php on line 43

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpoWCXpD' to '/home/chris/public_html/upload/Caleb.jpg' in /home/chris/public_html/upload.php on line 43
Sorry, there was a problem uploading your file. 




Any ideas????

---

### Post by JamieC on 2007-03-07
Do you have the correct permissions on /home/chris/public_html/upload/?

---

### Post by uamusa on 2007-03-07
Ok....talk about feeling like a complete moron.  In past years I'd built up such a mental block regarding Linux.....and that's been my biggest problem in learning it.......I keep trying to make things more difficult than they really are.  Thank You!

---

### Post by russellnation on 2008-01-03
thanx, is this a problem on .. say godaddy's hosting.

---

### Post by NICKKKKK on 2008-05-08
Hello, 

what exactly are the permissions for that? My folder has 777 permissions and although it works fine locally, it does not work on the host server :(

thanks
Nick

---

### Post by bolunmez on 2008-10-10
> **uamusa said:**
> Trying to implement and Upload form on my Web Server:

**upload.hmtl  :**

<form enctype="multipart/form-data" action="upload.php" method="POST">
Please choose a file: <input name="uploaded" type="file" /><br />
<input type="submit" value="Upload" />
</form> 

**upload.php  :**
<?php 
$currentdir = getcwd();

$target = $currentdir . "/upload/"; 
$target = $target . basename( $_FILES['uploaded']['name']) ; 
echo "Temp Location: $target_path<br>";
$temploc=$_FILES['uploadedfile']['tmp_name'];
echo "Temploc: $temploc<br>";

$ok=1; 

//This is our size condition 
if ($uploaded_size > 350000) 
{ 
echo "Your file is too large.<br>"; 
$ok=0; 
} 

//This is our limit file type condition 
if ($uploaded_type =="text/php") 
{ 
echo "No PHP files<br>"; 
$ok=0; 
} 

//Here we check that $ok was not set to 0 by an error 
if ($ok==0) 
{ 
Echo "Sorry your file was not uploaded"; 
} 

//If everything is ok we try to upload it 
else 
{ 
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))   //**THIS IS LINE 43**
{ 
echo "The file ". 
basename( $_FILES['uploadedfile']['name']). " has been uploaded"; 
} 
else 
{ 
echo "Sorry, there was a problem uploading your file."; 
} 
} 
?>


**What you get when you attempt to use the upload form  :**

Warning: move_uploaded_file(/home/chris/public_html/upload/Caleb.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /home/chris/public_html/upload.php on line 43

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpoWCXpD' to '/home/chris/public_html/upload/Caleb.jpg' in /home/chris/public_html/upload.php on line 43
Sorry, there was a problem uploading your file. 




Any ideas????

did you solve that ?? I 'm working to understand php at w3schools. when i tried this[example]("http://www.w3schools.com/php/php_file_upload.asp"), i took similar message as yours which you seeing below:
```

Warning: move_uploaded_file(transpix.gif) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/yeni/index.php on line 234

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpNwcYNk' to 'transpix.gif' in /var/www/yeni/index.php on line 234
Stored in: transpix.gif 

```

/var/www/yeni directory and sub directories are chmod 777.:confused:

---

### Post by Mexstang on 2009-05-25
I had this error w/my Godaddy account.>I just had to log into my account & use the File Manager in the Hosting Control Center to set the permissions to read & write for the folder which I was trying to upload to.

---

### Post by XxionxX on 2009-08-02
I had this problem as well. I am noob to linux and I didn't know that I needed to give special permissions to certain files. What are permissions and exactly how did you fix your problem?

---

### Post by tapas_mishra on 2009-12-18
I think that you need to set permissions of the directory so as PHP scripts can run with uid of user who has write permission or else in the case if the permissions are not such if they give write permission to user www-data they may give error.

---

### Post by boramay56 on 2010-04-11
**Warning**: move_uploaded_file(uye_avatarlar/69549560.png) [[function.move-uploaded-file]("http://ubuntuforums.org/function.move-uploaded-file")]: failed to open stream: Permission denied in **D:\inetpub\vhosts\gumusulus.com\httpdocs\yeni_uyelik.php** on line **263**

**Warning**: move_uploaded_file() [[function.move-uploaded-file]("http://ubuntuforums.org/function.move-uploaded-file")]: Unable to move 'C:\WINDOWS\Temp\php710D.tmp' to 'uye_avatarlar/69549560.png' in **D:\inetpub\vhosts\gumusulus.com\httpdocs\yeni_uyelik.php** on line **263**

plsease help me:(
 
my code is
 
 
$posted  = "resim1";
        if ($_FILES["resim1"]['name']){
        $filename=$_FILES["$posted"]['name'];
        $efilename = explode('.', $filename);
        $uzanti = $efilename[count($efilename) - 1];
        $uzantilar=array('jpg','png','gif');       
        $isim=rand(0,99999999);
        $yeniad = "".$isim.".".$uzanti."";
        $hedef1  = "uye_avatarlar/".$yeniad;
        move_uploaded_file($_FILES["$posted"]['tmp_name'],"uye_avatarlar/".$yeniad);
        }

---

### Post by bbbaldie on 2010-04-12
Wow, this thread just keeps on living! :P

You have Windows permissions issues. Allow your web user (exact name will be listed under local users and groups) read/write access to c:/windows/temp and c:/inetpub.

---

### Post by denilugito on 2011-03-30
By the way is there any permission security software in ubuntu (e.g. i'm using Fedora 14 so in my case it's called "SELINUX"). If your ubuntu version has similar application then i think you should configure it. 

I have the same problem in Fedora 14 and in my case, i just need to turn the SELINUX  "Off" of change it to the "Permissive" mode. The tutorial can be seen in [http://fedora-denilugito.blogspot.com/](http://fedora-denilugito.blogspot.com/)

---

### Post by x.algorithm on 2011-06-08
It's good that you have the function that stops php files from being uploaded, smart move.  However, you're going to have to be very careful with your permissions on the folder you're uploading files to. If you are using a database on that site with access to that folder, then I want to stress that you should include checks for other files, especially .sql files or .cgi files ( you may not have cgi enabled), we do this to prevent execution of scripts and the like.

As to the permissions problem, the folder you are trying to write to needs to be owned by same user that apache (webserver) is executed as.  Usually, at large hosting sites, that would be your username - it will be chroot jailed so your site is only affected by your code, and your code cant affect another site.

I suggest a permissions scheme of 0644 on the folder - on the server - you wish to upload to. The exact command is 'chmod 0644 yourdirectory'  If you're using a gui to change permissions such as in filezilla or wsftp, then you would tick the boxes for owner to write and read, but not execute.  All others (group and other) are read only.

I hope this helps with your problems, and happy coding.

x.algorithm

---

### Post by mydebug on 2012-03-08
Please change the following line of code:
$target = $currentdir . "/upload/"; 
 
to:
$target = $currentdir . "/upload"; 
 
I was having a similar problem and was able to solve using this alteration. 
 
Regards.

---

