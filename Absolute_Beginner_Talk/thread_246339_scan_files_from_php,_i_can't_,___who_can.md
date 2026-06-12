---
title: "scan files from php, i can't ,   who can?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by shyami on 2006-08-29
Hi everyone,

        i am trying this one, for one week

i am uploading some files through my php code,
i need to scan the files for virus information,


          some sites they referred clamav, so i installed that one
it is working well in command line, in code, i gave like this

<?php

$e= "testphp.php";
echo "<br>";
$g= exec("clamscan \"$e\"");
echo "Res is <br>";
echo $g;
?>

my output is 

Res is
Time: 1.732 sec (0 m 1 s)


from this i can't know anything......
How can i get the virus information? 


guide me! plzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz




with thanks
shyami

---

