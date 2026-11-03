# python-assignment
# Real-life project: Distance travelled by a car using the Trapezoidal Rule
# Student: Harsh Vardhan Sharma
#
# Problem: A car's speedometer is noted every few minutes. Speed keeps changing,
# so distance = speed x time cannot be used directly.
# Distance = area under the speed-time graph, which the Trapezoidal Rule finds.

def trapezoidal(x, y):
    # x = list of times (hours), y = list of speeds (km/h)
    total = 0
    for i in range(len(x) - 1):
        width = x[i + 1] - x[i]
        area = width * (y[i] + y[i + 1]) / 2    # area of one trapezium
        total = total + area
        print("Part", i + 1, ": area =", round(area, 3), "km")
    return total


print("===== DISTANCE FROM SPEEDOMETER READINGS =====")
n = int(input("How many readings? "))

time = []    # in minutes
speed = []   # in km/h
for i in range(n):
    t = float(input("Time (minutes) of reading " + str(i + 1) + ": "))
    s = float(input("Speed (km/h) at that time: "))
    time.append(t)
    speed.append(s)

time_hours = [t / 60 for t in time]     # convert minutes to hours

distance = trapezoidal(time_hours, speed)
total_time = time_hours[-1] - time_hours[0]

print("\nTotal distance travelled =", round(distance, 2), "km")
print("Average speed =", round(distance / total_time, 2), "km/h")


