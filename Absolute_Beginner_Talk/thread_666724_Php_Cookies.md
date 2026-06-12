---
title: "Php Cookies"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Gian_Piero on 2008-01-13
Hi, I have written a simple page (/index1.php) to try cookies to be set and to have them appear on the page when /index.php is launched.

The /index1.php is:
<?

$state= $_POST["state"]; 

if ($state=="") 
{    if (isset($_COOKIE["stcookie"]))
       { 
	$state=$_COOKIE["stcookie"]; 
	} 
}

else { 
setcookie ("stcookie",$state ,time()+(3600*24*60),"/") ;
     }

?>

<html>

<body bgcolor="#fbd50a">

<p>SAMPLE html text</p>
<form action="/index2.php" method="post">

<select name="state"> 

<?
$j="";  $ss=""; if ($ss==$state)  {    $j="selected"; }
          echo  "<option $j  value=\"$ss\">$ss\n</option>";
$j="";  $ss="ARIZONA"; if ($ss==$state)  {    $j="selected"; }
          echo  "<option $j  value=\"$ss\">$ss\n</option>";
?>
</select>

<input type="submit" value="Click here" style="background:lime;
 font-style:italic; font-weight:bold">

</form>
</body>

</html>


The called page is /index2.php:

<?

$state = $_POST["state"];  

 setcookie ("stcookie",$state ,time()+(3600*24*60),"/") ; 
 
?>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">

<html>

<head>

<title> Receiving page</title>

</head>
<body bgcolor="#fbd50a">

<p>THIS page receives the STATE and posts back to index1 page</p>

<form action="/index1.php" method="post">
<?
print "<input type='hidden'  name='state'  value='$state'>";
?>
<input type="submit" name="sub" value="Click here back to index1"
 style="background:lime;  font-style:italic; font-weight:bold">

</body>

</html>

When the state = "ARIZONA" is set, I expect that when launching the browser the drop list shows "ARIZONA".
Instead I get BLANK !
The strange thing is that if /index2.php is first launched, "ARIZONA" DOES appear on the list when /index1.php will be launched !!

I am a PHP/COOKIES beginner, could anybody help me ?
Cheers

Gian_Piero

---

### Post by Miademora on 2008-01-13
Your code works for me with IE and Firefox. Windowsclient, PHP5 on Server.

Maybe your browser is not allowing non-session-cookies or something?

Check in the preferences of firefox if the cookie actually gets set and what the contents are.

---

### Post by Gian_Piero on 2008-01-21
Thank you very much for your response.
Actually the coding seems to work in several different computers, but not in all.
There must be a timing problem, especially when the coding is run in slower computers.
There is a remedy on that: instead of opening the first page /index1, I first open another page that quickly diverts to the above page.
In this case the cookie works fine.
Probably it does not work when the script loading occurs earlier than fetching the cookie....??? 
If this is the case, how to speed up the cooking fetching ?
Thank you for any response on this !!
Gian_Piero

---

### Post by Gian_Piero on 2008-01-23
Maybe the remedy could be the opposite: to slow down the page loading instead of making the cookie fetching faster.
Maybe < body onload=.....>
???
Thank you

---

### Post by wilsonmuse on 2008-01-23
> **Gian_Piero said:**
> Maybe the remedy could be the opposite: to slow down the page loading instead of making the cookie fetching faster.
Maybe < body onload=.....>
???
Thank you

Well, some of your code is difficult to read and your problem difficult to understand. I kinda rewrote a similar page just as an example of cookie usage. If you have any questions please feel free to ask.

```
<?
if ($_POST['state']) {
    $state = $_POST['state'];
    setcookie("stcookie", $state, time()+(3600*24*60), "/");
}
elseif ($_COOKIE['stcookie']) {
    $state = $_COOKIE['stcookie'];
}
?>
<html>
    <body bgcolor="#fbd50a">
        <p>SAMPLE html text</p>
        <form action="index1.php" method="post">
            <select name="state">
                <option value="" <? if (!$state) { echo "selected"; } ?>></option>
                <option value="ARIZONA" <? if ($state == "ARIZONA") { echo "selected"; } ?>>ARIZONA</option>
            </select>
            <input type="submit" value="Click here" style="background:lime; font-style:italic; font-weight:bold">
        </form>
    </body>
</html>
```

---

### Post by Gian_Piero on 2008-01-26
Thank you for cleaning my coding, I must admit it looked untidy.
Meanwhile I found out something interesting:
When the "action" URL in the <form> tag is written in full form (like "http://www.URL.com/index1.php") the fetching the cookie sometimes does not occur (maybe because the form loading anticipates the fetching).
When instead the "action" field is in short (like "index1.php") then every thing works successfully !!
Cheers
Gian Piero

---

