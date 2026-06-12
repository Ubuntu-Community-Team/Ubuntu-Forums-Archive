---
title: "PHP Problems.."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Pioneer5000 on 2008-03-14
I got this from a windows guide:

```

<?php
	require($_SERVER ("DOCUMENT_ROOT") . "/Config/db_config.php");
	$connection = @mysql_connect($db_host, $db_user, $db_password) or die("error connecting");
		echo "connection is a success!";
?>

```

What is wrong with that? im guessing its the Document_Root part ?

---

### Post by Pioneer5000 on 2008-03-14
Nvm got it working (forgot the = ) but i have another question why can't i view the httpd.conf file for apache?

---

