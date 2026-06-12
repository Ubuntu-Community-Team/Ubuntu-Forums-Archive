---
title: "Difficultly with PHP"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-09-25
Hi,

When I run the below PHP program:
> <html>
<head>
<title>Listing 11.13 Writing and Appending to a File</title>
</head>
<body>
<div>
<?php
$fileName="test2.txt";
print "Writing to $fileName<br>";
$fp=fopen($fileName, "w") or die("Couldn't open $fileName");
fwrite($fp, "Hello world\n");
fclose($fp);
print "Appending to $fileName<br>";
$fp=fopen($fielName, "a") or die("Couldn't open $fileName");
fputs($fp, "And another things\n");
fclose($fp);
?>
</div>
</body>
</html>

then I get this error message:
> Writing to test2.txt

Warning: fopen(test2.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/listing11.13.php on line 10
Couldn't open test2.txt

Could you tell me why this error and how I can solve it?

Thanks,
L-B

---

### Post by bluefrog on 2006-09-25
looks to me like permission problems.
 away from my linux box but if I recall /var/www is owned by root.

your php is accessing it as www-data hence the problem.

workaround:
create a folder in /var/www/ change ownership to www-data and have your php write your test file in that folder

James

---

### Post by chuckyp on 2006-09-25
Well php would need permisions to write to whatever directory that text.txt is in.  It sounds like its setup improperly perhaps someone with more server experience could chime in.

---

### Post by indytim on 2006-09-25
Follow BlueFrog's advice.  You might as well give yourself ownership of /var/www as you will probably be inserting scripts into your root anyways.

Been there... done that...

IndyTim

---

### Post by lreyes6 on 2006-09-25
It's allways recomended to put 755 permissons on your php files most of the time this resolves permissons problems

---

### Post by linux-beginner on 2006-09-26
Could you tell me how I can change the permission of PHP to can run the above program?

---

### Post by lreyes6 on 2006-09-26
you do it like this ```
sudo chmod -Rv 755 /path/to/your/php/code
```[LIST]
[*]chmod - the command to change permissons
[*]-Rv - recursive and printing an output of every change
[*]what to change[/LIST]any questions... just ask ;)

---

