# ImageRecognitionUseCases
ImageRecognitionModelTest
Testing Dlib and Other models to test on sample images.... Please refer Python files for different test sets.
Basics are mentioned over here with Google Cloud using tesnsor flow environment....detailed test cases are elaborated in individual notebook and Python script files.

Face Recognition steps - 

Install library - 
---------------------

!pip install face_recognition

Upload images - 
------------------

from google.colab import files

uploaded = files.upload()

for fn in uploaded.keys():
  print('User uploaded file "{name}" with length {length} bytes'.format(
      name=fn, length=len(uploaded[fn])))


User - uploaded files -
----------------------------
User uploaded file "biden.jpg" with length 270753 bytes
User uploaded file "unknown.jpg" with length 13636 bytes


Upload known images - 
----------------------
image = face_recognition.load_image_file("biden.jpg")

find face location -
------------------------
face_locations = face_recognition.face_locations(image)

upload unknown face -
-----------------------

unknown_image = face_recognition.load_image_file("unknown.jpg")


biden_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([biden_encoding], unknown_encoding)


Image recognition result - Same person
-------------------------
# comparing same person as known and unknown with differnt images.

import face_recognition
known_image = face_recognition.load_image_file("biden.jpg")
unknown_image = face_recognition.load_image_file("unknown.jpg")

biden_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([biden_encoding], unknown_encoding)

print(results)

Image recognition result - different person
-------------------------
# comparing same person as known and unknown with differnt person image.

import face_recognition
known_image = face_recognition.load_image_file("biden.jpg")
unknown_image = face_recognition.load_image_file("unknown3.jpg")

biden_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([biden_encoding], unknown_encoding)

print(results)


Image recognition result - Same person (Pradeep) with different glasses
-------------------------
# comparing same person as known and unknown with differnt images.
import face_recognition
known_image = face_recognition.load_image_file("pradeep.jpg")
unknown_image = face_recognition.load_image_file("unknown3.jpg")

known_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([known_encoding], unknown_encoding)

print("Are they same person images - " + results)


Image recognition result - Same person (female)
-------------------------
# comparing same female person as known.
import face_recognition
known_image = face_recognition.load_image_file("babita.jpg")
unknown_image = face_recognition.load_image_file("unknown4.jpg")

known_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([known_encoding], unknown_encoding)

print("Are they same person images - " + results)

Image recognition result - Different person (female)
-------------------------
# comparing different female person.

import face_recognition
known_image = face_recognition.load_image_file("unknown4.jpg")
unknown_image = face_recognition.load_image_file("unknown5.jpg")

known_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([known_encoding], unknown_encoding)

print(results)





Image recognition three images
-------------------------------
Image recognition result - 
-------------------------
# comparing same person as known and unknown with differnt images.

import face_recognition
known_image = face_recognition.load_image_file("biden.jpg")
unknown_image = face_recognition.load_image_file("unknown.jpg")
unknown_image1 = face_recognition.load_image_file("unknown1.jpg")

biden_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]
unknown_encoding1 = face_recognition.face_encodings(unknown_image1)[0]

results = face_recognition.compare_faces([biden_encoding], unknown_encoding)
print(results)

results1 = face_recognition.compare_faces([biden_encoding], unknown_encoding1)
print(results1)


Output - 
-----------
[True]
[False]

Image recognition my images images
-------------------------------
import face_recognition
known_image = face_recognition.load_image_file("biden.jpg")
known_image1 = face_recognition.load_image_file("pradeep.jpg")
unknown_image = face_recognition.load_image_file("unknown.jpg")
unknown_image1 = face_recognition.load_image_file("unknown1.jpg")
unknown_image2 = face_recognition.load_image_file("unknown2.jpg")

biden_encoding = face_recognition.face_encodings(known_image)[0]
self_encoding = face_recognition.face_encodings(known_image1)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]
unknown_encoding1 = face_recognition.face_encodings(unknown_image1)[0]
unknown_encoding2 = face_recognition.face_encodings(unknown_image2)[0]

results = face_recognition.compare_faces([biden_encoding], unknown_encoding)
print(results)

results1 = face_recognition.compare_faces([biden_encoding], unknown_encoding1)
print(results1)

results2 = face_recognition.compare_faces([self_encoding], unknown_encoding2)
print(results2)
