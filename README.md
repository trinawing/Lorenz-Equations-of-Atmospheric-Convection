# Lorenz-Equations-of-Atmospheric-Convection

%Trina Wing
%Main Code

[X, Y, Z, T ]= lorenz_forward_eulers(0, 100, 1.01, 2, 20, .01);

%plot(T,X, 'd'); hold on;
%plot(T,Y, ':r*'); hold on;
%plot(T,Z, '--go')
plot(X,Z, '--r')
%title('Strange Attractor')
%title('Lorenz Equations of Atmospheric Convection ')
%legend(' in X', ' in Y', ' in Z' )

function [X,Y,Z, T] = lorenz_forward_eulers(a, b, x_0, y_0, z_0, h)

N = (b-a)/h +1;
X = zeros(N, 1);
Y = zeros(N, 1);
Z = zeros(N, 1);
T = a:h:b; 



X(1) = x_0;
x0 = x_0;
t0 = a;
Y(1) = y_0;
y0 = y_0;
Z(1) = z_0;
z0 = z_0;

for i = 2:N
    
    x = x0 + h*lorenz_rhs(t0, x0, y0);
    y = y0 + h*lorenz_rhs2(t0, x0, y0, z0);
    z = z0 + h*lorenz_rhs3(t0, x0, y0, z0);
    X(i) = x;
    Y(i) = y;
    Z(i) = z;
    x0 = x;
    y0 = y;
    z0 = z;
    t0 = t0 + h;
end
end
    
function dx = lorenz_rhs(t,x,y)

d = 10;
dx = d*(y-x);
end

function dy = lorenz_rhs2(t,x,y,z)

p = 28;
dy = x*(p - z) -y;
end

function dz = lorenz_rhs3(t,x,y,z)

b = 8/3;
dz = x*y - b*z;
end
