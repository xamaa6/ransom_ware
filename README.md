# ransom_ware
Simple Ransomeware Technique in C++

This is a simple technique to implement a ransomware in C++

Compiled on visual studio 2012

Tested on windows 7

How it works?

  Encryptor:
  
    * Encryptor first looks for the folder C:/Témp/
    * If it exists, it means the system is already encrypted with some AES key & the program shuts down. If the folder doesn't exist, the program will continue.
    * It will then find all the files on the system.
    * Encryptor will then encrypt the files (per folder, which helps in encrypting as much files as possible before the program is shutdown) using AES encryption (which is very slow for big files) with a random key of certain length.
    * It will then create a folder in C:/Témp/ which is similer to C:/Temp & saves the encryption key to this folder using name win.txt
    * It encrypts the file win.txt with XTEA encryption with specified keys and also renames it to win.jpg
    
  Decryptor:
  
    * Decryptor first looks for the folder C:/Témp/
    * Renames the file win.jpg to win.txt
    * Uses XTEA to decrypt the file
    * The file then contains the Decryption key for all the other files on the system
    * Finds all files & starts decrypting them.

  Additional Features:
  
    * Finds all files including hidden files.
    * Program can run in the background.
