Message-passing project configuration instruction
-----------------------------------------------------
Following below steps to prepare raspberry pi client
-----------------------------------------------------
1. Download Raspian, the Operating system that runs on Raspberry pi from this link . 
We used Raspian Buster with Desktop, Kernel version 4.19. Unzip the downloaded folder 2. Download Etcher, a software to flash the Operating system on the SD card 
Etcher 3. Flash the Operating system(the downloaded Raspian folder) on your SD card by using 
the Etcher software. 4. Insert the SD card into the SD card slot on the Raspberry pi. 5. Connect the Raspberry pi to monitor using Micro HDMI to HDMI cable. 6. Connect the Type C power cable to Raspberry pi. (this will Boot the pi, just like a 
computer) 7. Once Booted, you will see the Desktop screen. Navigate to the upper right side corner 
click on network options and select your local wifi network. Optionally you can also put a file named wpa_supplicant.conf in your SD card boot folder with the following configurations 
Ssid = local wifi name Psk = password to the wifi Country = country of your wifi provider 
This will add the wifi configuration to your raspberry pi in case you don’t have access to a monitor 
8. Check the IP address of the Raspberry pi using ipconfig. 9. You can SSH into the Raspberry pi from your computer, only if the two are on the same 
network 10. Put the client.py file, imagezmq folder onto using Raspberry pi. You can do this using a 
flash drive, SSH copy(cp), download from github. 11.Create Virtual Environment: Virtual environment give’s your pi a chance to 
share all binaries and os from your development local machine. So you can avoid work on pi’s os and binary library, which causes a lot of pain. 
a. pip install virtualenv b. Virtualenv -p python3 venv/ c. Source venv/Scripts/activate 12. Once you have your client code ready. Install all the dependencies required to execute 
the code. 
a. pip install imutils b. pip install opencv-contrib-python c. pip install zmq d. pip install numpy 13. Check if your Raspberry pi camera is working raspistill -v -o test.jpg 
This command will trigger the camera and capture a photo frame in 5sec. The photo names test.jpg will be stored in your root folder. 
14. Navigate to the directory where your client code exists and execute your client code with 
the command: 
python client.py --server-ip <SERVER_IP> 
Make sure you have your server running, and you know the ip address of your server. 

Following steps below to configure your server
--------------------------------------------------

1. Keep your server.py file, MobileNetSSD_deploy.caffemodel, 
MobileNetSSD_deploy.prototxt in one single folder on your server. 2. Install all the dependencies required to execute the code 3. In your server.py Supply the path you the two data training models are argument 
variables. 4. Set the appropriate confidence(0.3), montageW(4*1), montageH(100). Values 
supplied in parenthesis are what we used in your case. 
5. Fire up the server using the following command 
python server.py --prototxt MobileNetSSD_deploy.prototxt --model MobileNetSSD_deploy.caffemodel --montageW 2 --montageH 2 
6. Check the ip address of your server and use that when connecting client to server 7. Your server will start bringing in frames from each of your Pis. Each frame that comes in 
is passed through the MobileNet SSD 

