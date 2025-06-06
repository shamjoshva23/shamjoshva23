import cv2

# Open the webcam
cap = cv2.VideoCapture(0)

# Define video codec and output file
fourcc = cv2.VideoWriter_fourcc(*'XVID')
out = cv2.VideoWriter('recorded_video.avi', fourcc, 20.0, (640, 480))

print("Recording... Press 'q' to stop.")

while cap.isOpened():
    ret, frame = cap.read()
    if ret:
        out.write(frame)
        cv2.imshow('Recording - Press q to stop', frame)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break
    else:
        break

cap.release()
out.release()
cv2.destroyAllWindows()
