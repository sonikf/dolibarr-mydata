# DOLIBARR ERP & CRM MODULE FOR GREEK AADE MYDATA 

This Dolibarr module pushes invoices to AADE MyDATA

***
Έχει και όλες τις κατηγορίες της παρακράτησης φόρου όπως αναφέρονται στην ΑΑΔΕ. 

## Προσοχή: Δεν δουλεύει με πολλαπλά ΦΠΑ.

## Τρόπος λειτουργίας:

Ενεργοποιούμε στις ρυθμίσεις την παρακράτηση φόρου. Απενεργοποιούμε και ενεργοποιούμε το module.

Δημιουργούνται δύο extra fields τα εξής:

Extra field με κωδικό mydata_taxwh στα τιμολόγια τύπος price.

Θα πρέπει να συμπληρώνεται ώστε να στέλνει την παρακράτηση του τιμολογίου στην ΑΑΔΕ. Εάν δεν έχει συμπληρωθεί ή είναι 0 δεν στέλνει την παρακράτηση και το στέλνει το τιμολόγιο κανονικά (χωρίς).

Extra field me κωδικό mydata_taxwh_category τύπου λίστα

Εδώ έχει όλες τις κατηγορίες από το pdf της ΑΑΔΕ. Επιλέγοντας την κατηγορία που θέλετε (έχει περιγραφές) καταχωρεί τον κωδικό της και το στέλνει στο mydata. Η κατηγορία αποστέλλεται μόνον όταν έχει συμπληρωθεί το ποσό της παρακράτησης στο παραπάνω extra field.

pdf της ΑΑΔΕ σελ 47 (κατηγορίες παρακράτησης φόρου)
https://www.aade.gr/sites/default/files/2021-11/myDATA%20API%20Documentation%20v1.0.4_official_erp.pdf

Στις ονομασίες υπάρχουν translation strings. Τα ονομάζεται είτε στα extrafields του module invoice όπως θέλετε ή στις μεταφράσεις εάν θέλετε να έχετε πολλές γλώσσες.

Στο mydata tab του module φένεται το ποσό της παρακράτησης και η κατηγορία ανά τιμολόγιο. Εάν στην κατηγορία αναγράφει 0 σημαίνει ότι δεν έχουμε επιλέξει τίποτα. Εάν δεν έχουμε καταχωρίσει ποσό παραρακράτησης τότε η κατηγορία δεν αποστέλλεται ακόμα και εάν στο τιμολόγιο έχουμε επιλέξει κατηγορία. 


***
## Install module:
- If you get the module in a zip file (like when downloading it from the market place [Dolistore](https://www.dolistore.com)), go into
menu ```Home - Setup - Modules - Deploy external module``` and upload the zip file.


Note: If this screen tell you there is no custom directory, check your setup is correct: 

- In your Dolibarr installation directory, edit the ```htdocs/conf/conf.php``` file and check that following lines are not commented:

    ```php
    //$dolibarr_main_url_root_alt ...
    //$dolibarr_main_document_root_alt ...
    ```

- Uncomment them if necessary (delete the leading ```//```) and assign a sensible value according to your Dolibarr installation

    For example :

    - UNIX:
        ```php
        $dolibarr_main_url_root_alt = '/custom';
        $dolibarr_main_document_root_alt = '/var/www/Dolibarr/htdocs/custom';
        ```

    - Windows:
        ```php
        $dolibarr_main_url_root_alt = '/custom';
        $dolibarr_main_document_root_alt = 'C:/My Web Sites/Dolibarr/htdocs/custom';
        ```
